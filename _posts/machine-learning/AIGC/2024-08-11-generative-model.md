---
title: Generative Model
description: Write down description here.
author: yoyo
date: 2024-08-11 11:33:00 +0800
categories: [Artificial Intelligence, AIGC]
tags: [AIGC]
---

# Step 0: Initialize the model parameters
- Begin with an initial set of parameters. These parameters are often randomly initialized before the training process begins.

## Step 1: Forward pass (Generate data)
- Perform a forward pass using the current model parameters to generate new data instances.
- Mathematically, this can be represented as \( f(z) = f_\theta(z) \), where \( z \) is input to the model, and \( \theta \) represents the model parameters.

## Step 2: Calculate the difference between generated data and real data
- Calculate a distance metric \( d(p_1, p_2) \) which measures the difference between the probability distribution of the generated data and the real data.

## Step 3: Optimize the parameters to minimize the distance
- The objective is to adjust the model parameters \( \theta \) to minimize the distance between the generated data distribution \( p_{f_\theta}(z) \) and the real data distribution \( p_{data} \).
- This is typically achieved using optimization techniques such as gradient descent, and the optimization is often framed as \( \min_\theta d(p_{f_\theta}(z), p_{data}) \).


