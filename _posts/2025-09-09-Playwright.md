---
layout: post
title: Using PlayWright to Track Website Changes
date:   2025-09-09 17:30:20
description: Using PlayWright to collect dynamic infromation from websites.
tags: ChangeDetection.io, PlayWright
categories: Web Scraping
---

# ChangeDetection.io

ChangeDetection.io is an application that you can install as a docker image, and run as a container allowing you to use the application within your browser via localhost.

This is an interesting tool that allows you to track changes in websites. These changes that we are tracking are often for the purpose of tracking price changes or new news headlines etc. 

The way changedetection works is by itteratively taking a 'snapshot' of the webpages html format or the javascript and comparing that snapshots differences to the past historical pages to indicate changes.

Many websites employ tactics to prevent webscraping, changedetection can aid in the process of circumnavigating these strategies. One strategy is by using javascript to have dynamic information rather than a static html page, making it more difficult to scrape, when pages use this technique we can employ PlayWright.

## PlayWright

Not all sites have static html webpages, actually most have some sort of dynamic features that can make increasingly difficult to scrape. These are often created and displayed using javascript. 

In order to take a 'snapshot' of these more dynamic pages we need to use another tool such as PlayWright.