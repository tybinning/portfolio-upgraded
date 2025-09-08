---
layout: post
title: Avoiding Anti-Webscraping Strategies
date:   2025-09-08 12:00:21
description: Different Strategies to avoid anti-webscraping strategies within changedetection.io
tags: ChangeDetection.io, PlayWrite, Proxy Servers
categories: Web Scraping
---

# Introduction

# ChangeDetection.io

ChangeDetection.io is an application that you can install as a docker image, and run as a container allowing you to use the application within your browser via localhost.

This is an interesting tool that allows you to track changes in websites. These changes that we are tracking are often for the purpose of tracking price changes or new news headlines etc. 

The way changedetection works is by itteratively taking a 'snapshot' of the webpages html format or the javascript and comparing that snapshots differences to the past historical pages to indicate changes.

Many websites employ tactics to prevent webscraping, changedetection can aid in the process of circumnavigating these strategies.

## Internet Proxy Server

Proxy servers allow you to avoid being blocked by executing your scripts through a different IP address. Your IP address is a unique address assigned to your computer. If a site realize that your computer was accessing their page every 30 seconds for the last 10 days their is a strong likelihood that the site will think you're a bot. Going through a proxie/ different IP address it makes it harder to deterine.

## PlayWright

Not all sites have static html webpages, actually most have some sort of dynamic features that can make increasingly difficult to scrape. These are often created and displayed using javascript. 

In order to take a 'snapshot' of these more dynamic pages we need to use another tool such as PlayWright.