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

Many websites employ tactics to prevent webscraping, changedetection can aid in the process of circumnavigating these strategies. Here are some tactics that we can use to circumnavigate these tactics.

## Internet Proxy Server

Proxy servers allow you to avoid being blocked by executing your scripts through a different IP address. Your IP address is a unique address assigned to your computer. If a site realize that your computer was accessing their page every 30 seconds for the last 10 days their is a strong likelihood that the site will think you're a bot. Going through a proxie/ different IP address it makes it harder to deterine.

## PlayWright

Not all sites have static html webpages, actually most have some sort of dynamic features that can make increasingly difficult to scrape. These are often created and displayed using javascript. 

In order to take a 'snapshot' of these more dynamic pages we need to use another tool such as PlayWright.


# Headless Browser

A headless browser is a browser that doesn't need a UI as it runs in the background via your terminal.
Used largely for automating processes.

# CAPTCHA

I'm sure you have experience clicking on a website and all of a sudden it requires you to fill out a CAPTCHA puzzle where you are required to click images that have a bicycle in them or some other item.

There are services that can aid to help with this as well through changedetection.io, however most of these services are paid. 