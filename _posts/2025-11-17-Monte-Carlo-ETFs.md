---
layout: post
title: High Yeild Dividend ETF Monte Carlo Simulation
date: 2025-11-17
description: Monte Carlo Simulation with High Yeild Dividend ETF's
categories: Finance, Monte Carlo
giscus_comments: true
related_posts: false
---

# Background

A Roth-IRA of a Roth- Individual Retirement Account is an investment account for post-taxed income, where the gains are not taxed. 
General retirement strategies is to place your money in Index Funds, or Exchange Traded Funds. Which are funds that give you shares of multiple stocks, diversifying your funds through multiple stocks. 

# Introduction

Currently I've been focused on preparing for retirement. I have always heard that there is no replacement for time within investing due to the concept of compound growth. While I was doom scrolling I read a post with a financial guru "not" giving financial advice (for legal reasons), he said something along the lines of investing your funds within certain high yield dividend etf's to increase the compounding effects for growth. 

For my personal retirement account, I have wanted to know whether this strategy would perform better than other strategies of investing in other index funds. When looking at different index funds their growth seems to significantly larger than that of the high yeild dividend etfs. 

For our Monte Carlo simulation we will set two strategy's one focusing on a strategy involving a four High Yeild Dividend ETF's and the other focusing on the basic indexes.
Our goal is to end with a probability distribution of my retirement account by the time I am ready to retire, and compare the resulting distributions of each strategy.

We are going to compare our simulations output to the compound interest formula output.

# Compound Interest Formula

$$
A = P(1 + (r/n))^nt
$$

where: 
    - **A** : Final **A**mount
    - **P** : Principal Amount, amount starting with
    - **r** : annual interest rate
    - **n** : number of compounding periods

## Compound Interest Rate with Monthly Contributions

$$
A = P(1 + (r/n))^nt + PMT[((1 + r/n)^nt - 1)/ r/n]
$$

where 
    - all variables are the same
    - PMT : regular monthly payment

