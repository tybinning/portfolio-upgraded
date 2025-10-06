---
layout: post
title: Predicting Combine Hopper Fill Times
date:   2025-09-08 12:00:21
description: 
tags: Agriculture, Spatial, Time-Series
categories: Agriculture, Spatial, Time-Series
---

# Introduction

Due to a number of factors I've had the oppurtunity to work with my family during harvest this fall. My primary task is to drive the grain cart. For those of you that don't know, the grain cart driver is tasked with driving a tractor attacted to the grain cart running back and forth collecting grain from each combine and unloading the grain into the semi-truck by the field entrance. The primary purpose of this job is to allow the combine opperators to use their time as efficient as possible collecting grain from the field. If you weren't using a grain cart, a majority of your time would be spent in transportation to and filling the semi-truck. 

In our family opperation we currently use two combines to speed things up. Running back and forth from the semi to either combine often feels as though the timing is mismatched. By the time I am filled and unloaded, the other combine already seems to be waiting on me. Another common problem is attempting to determine where I need to be to unload the combine at a particular time, this can cause logistical issues as often times their are obstacles preventing from traveling different paths.

My project that I want to create will predict when each combine is filled, and where the combine will be when it is filled.

There are a variety of variables that can be useful to our model. Heres a few listed out and some of the reasoning behind them:

Factors that can determine speed: 

- Temperature
- Grain Type
- Grain Mosture
- Roughness of terrain

Factors determining course:

- obstactles
- other combine
- ditches 

Other Factors:

- head size
- time since last rain
- operator
- time since last fill
- outliers: Ex. ( breaking down, lunch breaks?, funerals, rain, etc. )
- direction/ which side will the auger be on?
- ratio of field parameter to acres? : could be important in indicating amount of twists and turns for size?

Field factors:

- roughness of terrain
- yeild output: a feild that yeilds more will have more fills. 
- areas of higher output?

# Realistic expectations of Project

This project is going to be largerly used/ predicted on simulated data. The reason for this is to create a basic model/ and idea on how we could formulate this with gps data and tracking other indicators.

Currently the capital to purchase and building these connections is lacking. We need to create a proof of concept before determining whether continuing this project may be worth it. 

However our goal is to create a model that can predict the a general spatial location on a map based off a form of time-series model that determines when each combine will fill up. We can track all of our conditions, time to fill as well as our fields that we are at farely easy. However the locations/ pattern of the combines and speeds maybe a little harder to determine. We can ask the combine opperator their speeds. 

This will be largely a time-series model with a demonstration of how we could apply that model to a spatial model with predicting a predefined path.

# Unrealistic Applications/ Expections

Using GPS streaming data paired with sensors and IoT to determine location, time, and best possible location for the grain cart driver to be, all displayed on a dashboard in the cab of the tractor.

The connection of sensors determining how full, speed, and location would largely increase the predictive applications of this model. However these would take extra capital and organizational cooperation.

# Project Structure/ Outline


# Notes

I'm excted for this project as I believe that it will display a connection of passion, usefulness, and uniqueness connecting to my roots.