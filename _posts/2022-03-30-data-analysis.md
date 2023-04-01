---
layout: post
title: "Exploring the Data From Top 207 Motivational Self-Help Books!"
author: Steven Garcia
description: This blog summarizes the exploratory data analysis I performed on the data set I created in the previous blog.
image: /assets/images/analysis.jpg
---

## Introduction

Data is usefull because it can be interpreted to find insights that otherwise wouldn't have been found. In the previous post, I webscrapped top 207 self-help books from amazons website. I cleaned and formatted the data to make it ready for analyziation.

In this post I'll review the EDA (Exploratory Data Analysis) that I conducted for the price, number of reviews, and rating column. Now a brief refresher on what EDA is.
![Figure] INSERT GENERIC IMAGE HERE

EDA helps to identify patterns, anomalies, and relationships in the data that may not be obvious at first glance. EDA can be used to explore various types of data, including numerical, categorical, and textual data. Some common techniques used in EDA include histograms, scatter plots, box plots, correlation matrices, and data clustering.

# A Few Visualizations

As I was cleaning the data, I noticed that a lot of the books were listed with a price of 0. This is because the book is free with an audible subscription. I thought it would be interesting to see how many of the top 207 books are free with a subscription and it turns out that majority of books are available with an audible subscription. It would be interseting to see if books of other genres are mostly free as well.

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/costfree.png)

All of the books have a price associated with them if you didn't buy an audible subscription but this visualization shows us that Amazon is really encouraging their users to buy into the subscription.

For the next part of my analysis I wanted to focus on the ratings the books. To my suprise none of the books had an average rating of less than four stars! There wasn't a perfect score but there was quite a few that were rated 4.9/5.

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Average%20rating%20for%20books.png)

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Hist%20of%20rating.png)

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Hist%20of%20price.png)

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Price%20vs%20Rating%20Scatter.png)

# Correlation Matrix

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/corr.PNG)

# What's Next?
