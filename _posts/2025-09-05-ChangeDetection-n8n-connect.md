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


