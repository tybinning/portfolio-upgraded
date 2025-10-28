---
layout: page
title: Simple RAG App
description: Allows users to upload PDF's and ask the chatbot a question about the document.
img: assets/img/12.jpg
importance: 1
category: work
---

# Introduction

I wanted to build a simple streamlit app that allows me to upload documents in PDF form and allows me to ask questions about them. However I didn't want to ask a question about one topic and have the RAG pull information from unrelated documents.

Below you can see our simple streamlit app that allows you to discuss different documents that are uploaded.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/simpleRAGApp.png" title="Demo Screenshot image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Demonstration User Interface.
</div>

# User Interface Description
First you need to enter your HuggingFace Token inorder to access this app.

In order to control which documents I want to interact with via the chatbot, I added a sidebar that allows for the user to add "topics" and "subtopics" which is essentially creating a folders or nested folders. 

From there I created another two more sections within the side bar one allowing you to upload documents into the folder of your choice and the other for specifying what scope or what folder of documents you want the chatbot to look at. 

Upon further inspection you can see tags above the chatbot box. These are meant to display your current directory or scope, serving as a reminder of what documents the chatbot can access.


# Technical Details

For our chatbot I decided to use Mistral mainly because this model is open source and provides comparively better conversation styled answers.

For our RAG I used Chroma to build our vector database, when uploading a document our app adds metadata to the chunks detailing the files location within our folders. This allows us to dictate our similarity search by using the filter parameter to limit the documents reviewed.

## Streamlit App
Inorder to create a MVP I used Streamlit which allows for the creation of simple application within python. 

This allowed for more focus on our model, retreive augemented generation pipeline structure, and simple interface formatting.

## RAG 

I created a class named RAG to keep our app.py script clean and easy to read. This class has multiple methods that aid in our rag pipeline: 
{% raw %}
```python
class RAG:
    def __init__(self, hf_token):
        """
        initalizes our llm, vector db, embedding model, and stores our messages.
        """

        login(hf_token)
        self.client = InferenceClient(
            model="mistralai/Mixtral-8x7B-Instruct-v0.1"
            )

        base_dir = os.path.dirname(os.path.abspath(__file__))
        db_path = os.path.join(base_dir, "..", "db", "vectorstore")
        os.makedirs(db_path, exist_ok=True)

        self.chroma = chromadb.PersistentClient(path=r"db\vectorstore")
        self.collection = self.chroma.get_or_create_collection("docs")
        self.splitter = RecursiveCharacterTextSplitter(
            chunk_size=500,
            chunk_overlap=100,
        )
        self.embedding_model = SentenceTransformer("all-MiniLM-L6-v2")
        self.messages = [
            {
                'role':'system', 
                'content':'''You are a helpful assistant that answers questions based on provided documents.
            Use only the information in the context below to answer.
            If the answer is not found, say you don’t know.'''
            }
        ]

    def pdf_reader(self, file):
        """
        Opens and reads the pdf producing a text output
        """
        with pdfplumber.open(file) as pdf:
            text = ""
            for page in pdf.pages:
                page_text = page.extract_text(x_tolerance=2, y_tolerance=2)
                if page_text:
                    text += page_text + "\n"
        return text


    def adding_chunked(self, full_text: str, doc_name:str, topic: str, section: str= "", subsection: str = ""):
        """
        This function:
        1.) Splits text into chunks
        2.) creates chunk id
        3.) Encodes Chunk
        4.) Adds Chunk to our Chroma Vector DB and adds meta data relating to its topics.
        """

        if type(subsection) == list:
            subsection = subsection[0]

        chunks = self.splitter.split_text(full_text)  
        existing_ids = set(self.collection.get()['ids'])

        for i, chunk in enumerate(chunks):
            chunk_id = f"{topic}_{doc_name}_chunk_{i}"

            if chunk_id in existing_ids:
                continue
            
            embedding = self.embedding_model.encode(chunk)


            self.collection.add(
                documents=[chunk],
                embeddings=[embedding.tolist()],
                ids=[chunk_id],
                metadatas=[{
                    "document": doc_name,
                    "topic":topic,
                    "section": section,
                    "subsection":subsection,
                    "chunk_index": i
                    }]
                    )
            
    def query_context(self, query:str, topic: str = "", section: str = "", subsection: str = "", document: str= ""):
        """
        Filters by chosen topics to execute similarity searches.
        """
        filters = {
            "topic":topic,
            "section":section,
            "subsection":subsection,
            "document":document
        }
        filter_df = {k: v for k, v in filters.items() if v}

        embedding = self.embedding_model.encode(query)

        results_lst = []
        for k, v in filters.items():
            results = self.collection.query(
                query_embeddings=[embedding.tolist()], 
                n_results=3,
                where={k: v}
                )
            results_lst.append(results)
        
        all_docs = []
        for res in results_lst:
            all_docs.extend(res["documents"][0])

        if not all_docs:
            return "No relevant context found."


        context = "\n".join(all_docs)
        return context

    def rag_format(self, query:str, context:str):
        """
        Formats our context within our template for our LLM.
        """
        prompt = f"""
            RAG Returned Context:
            {context}

            Question:
            {query}
        """
        return prompt

    def generation(self, formated_prompt):
        """
        Generates an answer from our formatted prompt.
        """
        # adds conversation to the model
        self.messages.append(
            {
                'role':'user', 
                'content':f'{formated_prompt}'
            }
            )
        
        response = self.client.chat_completion(self.messages, max_tokens=100)
        # extracts txt from the model
        respomse_txt = response.choices[0].message.content

        

        # add assistant response to the model
        self.messages.append({'role':'assistant', 'content':f'{respomse_txt}'})
        
        return respomse_txt

    def ask(self, query, topic="", section="", subsection="", document=""):
        """
        Combines all of our conversational/ output functions to generate a text output. 
        Creating simplification within our app.py script.
        """
        context = self.query_context(query, topic, section, subsection, document)
        formatted = self.rag_format(query, context)
        return self.generation(formatted)
```

{% endraw %}

# Next Steps

This is a good format is a good starting point that allows me to continue building into specialized areas or increase complexity. Right now the model is simplictic and produces some errors or hallucinations. 

Here are some thoughts on how to expand from this project: 

- Fine-tune the large language model using a Low Rank Adaptation Model (LoRA)
- Adding multimodal features for our RAG, and chat allowing the chat to pull images from documents on demand
    - This would need an adjusted PDF processing method to  automatically collect and identify the image and add metadata like captions.
- There is the availability to create agents with access tools

There are lots of directions I can go with this simple app that gives me a good platform to experiment and grow my skills.