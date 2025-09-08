---
layout: post
title: Connecting ChangeDetection.io to n8n
date:   2025-09-05 12:00:21
description: Connecting changedetection.io to n8n via AppRise style webhooks
tags: ChangeDetection.io, n8n, AppRise, Webhooks
categories: Web Scraping, Workflow Automation
---

# Introduction
We are currently working within a project for the purpose of automating a price website tracking workflow.

We are using changedection.io via a Docker Container Instance. 

We need to integrate our changedetection.io differences into our **n8n** automation workflow.

We plan to do this by using webhooks.

# ChangeDetection.io

ChangeDetection.io is an application that you can install as a docker image, and run as a container allowing you to use the application within your browser via localhost.

This is an interesting tool that allows you to track changes in websites. These changes that we are tracking are often for the purpose of tracking price changes or new news headlines etc. 

The way changedetection works is by itteratively taking a 'snapshot' of the webpages html format or the javascript and comparing that snapshots differences to the past historical pages to indicate changes.

Many websites employ tactics to prevent webscraping, changedetection can aid in the process of circumnavigating these strategies.

# n8n 
n8n is a useful low-code tool to create workflow automations. Currently for this project we will be using n8n to collect data from changedetection.io modfy the data and display it in a dashboard.


# Connection ChangeDetection.io to n8n

In order to connect ChangeDetection.io to n8n we need to add a webhook node to our n8n workflow.

If you'll look below you can see an example of the webhook node added into our n8n canvas.

![Webhook Node](webhook-n8n-node.png "Webhook Node")

When double clicking into the webhook page we should get the following details, that we can adjust.

![Webhook Node Details](portfolio-upgraded\assets\img\webhooknode-opened-empty.png "Webhook Node")

We need to change the 

In order to test our webhook connection we need to create a webtracking instance within changdetection.io. We can do this by entering the url of a webpage that we want to monitor, I choose this blog within my portfolio website.

![Change Detection](assets/img/changedetection-enter-url.png "CHange Detection")

If you click edit and manuever over to the notifications tap, you can enter your webhook address, replacing the `https://` with `json://` this uses AppRise formating, dictating the type the format of data being sent. 

As you can tell below the Notification body has a JSON styled structure pairing "changes" with {{diff}} which gives the values that have been changed. When clicking on 'show toke/ placeholders' below the notification text box you can see the different options that you could include within your notification text box.

![Notifications](portfolio-upgraded/assets/img/changedetection-enter-notif.png "Webhook Node")

Within the notifications tab we can test the webhook by clicking 'Send test notification', it is important to node that inorder to recieve the following message in the image below you need to have clicked test within your webhook node in n8n before clicking test within change detection.io. 

![Webhook Node Testing ](C:\Users\tybin\OneDrive\Desktop\portfolio-upgraded\assets\img\webhooknode-open-full.png "Webhook Node")

Looking in the body and message schema from our test, you can see the output from the test meaning you have a successful connection.