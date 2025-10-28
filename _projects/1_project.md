---
layout: page
title: Simple Streamlit Document RAG App
description: Allows users to upload PDF's and ask the chatbot a question about the document.
img: assets/img/12.jpg
importance: 1
category: work
---

# Introduction

I wanted to build a simple streamlit app that allows me to upload academic pdf's and lets me ask questions about them. However I didn't want to ask a question about one topic and have the RAG pull information from unrelated documents. 

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



# Next Steps

This is a good format is a good starting point that allows me to continue building into specialized areas or increase complexity. Right now the model is simplictic and produces some errors or hallucinations. 

Here are some thoughts on how to expand from this project: 

- Fine-tune the large language model using a Low Rank Adaptation Model (LoRA)
- Adding multimodal features for our RAG, and chat allowing the chat to pull images from documents on demand
    - This would need an adjusted PDF processing method to  automatically collect and identify the image and add metadata like captions.
- There is the availability to create agents with access tools

There are lots of directions I can go with this simple app that gives me a good platform to experiment and grow my skills.