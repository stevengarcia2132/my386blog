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

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/chart.jpg)

EDA helps to identify patterns, anomalies, and relationships in the data that may not be obvious at first glance. EDA can be used to explore various types of data, including numerical, categorical, and textual data. Some common techniques used in EDA include histograms, scatter plots, box plots, correlation matrices, and data clustering. If you're intersted in learning more about EDA this is a great post about it! [Blog](https://towardsdatascience.com/exploratory-data-analysis-8fc1cb20fd15)

# A Few Visualizations

As I was cleaning the data, I noticed that a lot of the books were listed with a price of 0. This is because the book is free with an audible subscription. I thought it would be interesting to see how many of the top 207 books are free with a subscription and it turns out that majority of books are available with an audible subscription. It would be interseting to see if books of other genres are mostly free as well. All of the books have a price associated with them if you don't buy an audible subscription but this visualization shows us that Amazon is really encouraging their users to buy into the subscription.

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/costfree.png)

I continued my exploration of the books with and without price by seeing how their ratings comapred. I found out the average rating for the books that are free with a audible subscription are about the same for those that aren't free. This shows that the books that come with the Audible subscription are not lower tier books by any means. The difference between the two ratings is .3 percent which when accounting for an average rating out of 5 that doesn't make much of a difference.

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Average%20rating%20for%20books.png)

A question I had about the data was how it was distributed. So i created the figure below which displays a histogram of the ratings. To my suprise none of the books had an average rating of less than four stars! There wasn't a perfect score but there was quite a few that were rated 4.9/5. A majority of the book had an average rating of 4.8 out of 5. It would be interesting to compare this data with the average rating of other genres of books on amazon's website.

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Hist%20of%20rating.png)

I thought it would be interesting to examine how the price of the 207 books was distributed so i created another histogram of the price column. As you can see a majority of them are listed at 0 because of the audbile subscription. Most of the books seem to be clustered around the 12 to 15 dollar range which is reasonably priced. However, there were two outliers in the data set. One book was priced a bit more than 40 dollars and the other a bit more than 50 dollars. Since these were the only two points they probably didn't affect the average too much.

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Hist%20of%20price.png)

Along with looking at the price variable, I was curious if rating had an effect on price. The scatterplot below shows rating plotted alongside price. It was pretty clear from the previous grapsh that most of the books were rated highly so regardless of the price, any book would be a good one. After plotting the data I also made a correlation matrix between the numeric variables and saw that there isn't much of a relationship between price and rating. This conclusion was also supported by the previous graphs

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/Price%20vs%20Rating%20Scatter.png)

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/corr.PNG)

# Conclusion

So from the analysis we discovered that most of the books on Amazons top motivational books are free with an audible subscription and most of the books are rated above 4.6 stars. If you're intersted in seeing the code i used for this visualizations you can view it [here](https://github.com/stevengarcia2132/WebScrape-Amazon)

EDA is just the beginning of the analysis so stay tuned to see what I discover next with this data set!
