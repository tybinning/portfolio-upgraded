---
layout: post
title: Real Estate Price Prediction
date:   2025-09-08 12:00:21
description: 
tags: Real Estate, Spatial, Time-Series, Prediction
categories: Real Estate, Spatial, Time-Series
---

# Introduction

I have been interesting in Real Estate investing, there is a strategy in real estate investing that combines multiple strategies. Here's how it works, you buy a property, flip it (repair damages), rent the property out for five years, after 5 years sell and move on to the next property.

There are a multiple concerns of uncertainty within this strategy:

- How much can you expect to charge for rent after rennovating the property?
    - What improvements generate the highest change in rent?
    - What are people willing to rent in certain spatial areas? (Is there a price cap? -> this could limit your renivations.)
    - How does our rent prices compare to competitors in the area?
- How will the properties value change in five year or at the point you plan on selling?
    - What economic changes can cause the prices to change?
- How do I choose the right property ?
    - How do I know the property will be profitable?
        - Create a Monte Carlo simulation to give a probability distribution of profitability
- Monte Carlo Simulation Variables
    - There will be tons of variables to randomize, however the distributions of these different values will need to be based on past data, this could be rather difficult for different variables
    - Important Variables within Real Estate market:
        - 