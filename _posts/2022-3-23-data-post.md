---
layout: post
title:  "207 Different Perspectives on How to Improve yourself"
author: Steven Garica
description: Web Scraping the top 207 motivational self-help books from Amazon's website!
image: /assets/images/growth.jpg
---

I read my first self-improvement book in the summer of 2022. The book is called Greenlights by Matthew McConaughey and since then, I've been hooked on learning the little tricks that helped people be successful in their life. If you're feeling stuck, lost, or unsure of how to improve your life, reading a self-help book can be a game-changer. 

I know firsthand how valuable the insights and guidance in these books can be. They offer practical tools, actionable steps, and uplifting messages to help you shift your mindset, overcome obstacles, and create the life you want. Whether you're looking to improve your relationships, boost your confidence, or find more purpose and fulfillment, there's a self-help book out there that can help you on your journey. So don't hesitate to pick one up and give it a chance - it could be just the inspiration you need to take your life to the next level!



### Part 1: Getting the Data
---

## Finding the Correct Page

The first thing I did was navigate to the where all the products are listed on a page. Each page displays around 15 products so the important thing is to find the page that  lets you navigate to all the available pages. You'll know you on the right page when it looks like the images below.  

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/amazon.png)
![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/pages.jpg)

When you find the correct page you want to save all the html code into a file. This can easily be done by pressing Ctrl+ '+' + s. With all the HTML code for that page saved it's time to move on to the coding! 



## Scraping the page
Below is all the code I used to scrape the title, number of reviews, rating,price and image link. Once you find the HTML code that represent

```
import json
from bs4 import BeautifulSoup

# read the index.html file
with open('index.html', 'r',encoding =  'utf-8') as f:
    html = f.read()

# parse the html with BeautifulSoup
soup = BeautifulSoup(html, 'html.parser')

# find all divs with the specified class
divs = soup.find_all('div', {'class': 'sg-col-20-of-24 s-result-item s-asin sg-col-0-of-12 sg-col-16-of-20 sg-col s-widget-spacing-small sg-col-12-of-16'})

# initialize an empty list to store the results
results = []

# loop through the divs and extract the desired information
for div in divs:
    # find the image link
    img = div.find('img', {'class': 's-image'})
    link = img['src'] if img else ''
    
    # find the title
    title_span = div.find('span', {'class': 'a-size-medium a-color-base a-text-normal'})
    title = title_span.text if title_span else ''
    
    # find the rating
    rating_span = div.find('span', {'class': 'a-icon-alt'})
    rating = rating_span.text if rating_span else ''
    
    # find the price
    price_span = div.find('span', {'class': 'a-price-whole'})
    price = price_span.text.strip() if price_span else ''

    # find the num of reviews
    review_span = div.find('span', {'class': 'a-size-base s-underline-text'})
    review = review_span.text if review_span else ''

    # add the results to the list
    results.append({
        'link': link,
        'title': title,
        'rating': rating,
        'price': price,
        'review': review
    })

# write the results to a json file
with open('data13.json', 'w') as f:
    json.dump(results, f)

```
The first step was finding the class that contained the info for each product. Once i found what the name of the class was called, I searched for the variables I was interested within that class. 


 I executed this code many times after I saved the next page of products as the index file. Every time I moved from product page one to product page two I edited one of the last lines of the work.py file and added 'data2.json'. When i got to the 13 page of the product the bottom line read 'data13.json'.


### Part 2 Reading and Cleaning the Data
---

## Json, Json and More Json files

After running the code above many times, i ended up with 13 json files of data!

![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/jsons.png)

The next step was to get the data from each of these files and add them a dataframe. Luckily this part was much more straight forward! The hardest part was finding out how to read all the json files in one location. 

```
import os
import pandas as pd

# Set the directory containing the JSON files
directory = 'C:/Users/tinom/Downloads/'

# Get a list of all JSON files in the directory
json_files = [f for f in os.listdir(directory) if f.endswith('.json')]

# Read each JSON file into a Pandas DataFrame
dfs = []
for json_file in json_files:
    filepath = os.path.join(directory, json_file)
    df = pd.read_json(filepath)
    dfs.append(df)

# Concatenate the DataFrames into a single DataFrame
merged_df = pd.concat(dfs, ignore_index=True)
```

## Final touches
After I read them all into the merged_df it was time for the fun part! Cleaing and getting the data ready for analysis. This involved converting the numeric variables into numeric types instead of strings. 

```# create a new column called "rating_value"
merged_df['rating_value'] = merged_df['rating'].apply(lambda x: float(x.split()[0]))

merged_df.drop('rating', axis=1, inplace=True)
merged_df['review'] = merged_df['review'].str.replace(r'[\(\)]', '')
original_columns = merged_df.columns.tolist()
new_col = ['title','review','price','rating_value','link']
new_df = merged_df.reindex(columns=new_col)
new_df.to_csv("self-help books",index = False)
```

After finding, scraping and cleaning the data my table came out like this!
![Figure](https://raw.githubusercontent.com/stevengarcia2132/my386blog/main/assets/images/table.png)

Now that I have data that can be manipulated I'm ready to conduct exploratory data analysis and find correlations and trends in the data!

The code used to make this dataset can be found in my github repository here. 

https://github.com/stevengarcia2132/WebScrape-Amazon

Data was combined with tables from 

https://www.amazon.com/s?i=stripbooks&bbn=4736&rh=n%3A283155%2Cn%3A4736%2Cn%3A4744%2Cp_72%3A1250221011&dc&content-id=amzn1.sym.d3975239-6bd6-4ac7-88a5-1781bd35460e&pd_rd_r=34cd4b4c-e80e-43ba-9fc9-1ceeba0d8910&pd_rd_w=y9tOF&pd_rd_wg=yE1lI&pf_rd_p=d3975239-6bd6-4ac7-88a5-1781bd35460e&pf_rd_r=GXJQNQ4RFHP3WZ4MA4RH&qid=1679032402&rnid=4736&ref=sr_pg_1