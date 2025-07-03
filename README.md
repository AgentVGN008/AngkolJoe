# AngkolJoe
"Python projects and scripts developed by agentVNG008. This repository contains a collection of Python code for an extract and summarize data from the top 10 viral social medias. 
import requests
from bs4 import BeautifulSoup

# Specify the URL of the Social Media website
url = 'https://www.socialmediawebsite.com/trending'

# Send a GET request to the URL
response = requests.get(url)

# Parse the HTML content of the webpage
soup = BeautifulSoup(response.text, 'html.parser')

# Find all the trending content items on the webpage
trending_content = soup.find_all('div', class_='trending-item')

# Initialize lists to store the information of the top 10 trending content items
top_10_trending = []
count = 0

# Loop through each trending content item and extract relevant information
for item in trending_content:
    if count < 10:
        title = item.find('h2').text
        rating = item.find('span', class_='rating').text
        creator = item.find('p', class_='creator').text
        synopsis = item.find('p', class_='synopsis').text
        
        content_info = {
            'title': title,
            'rating': rating,
            'creator': creator,
            'synopsis': synopsis
        }
        
        top_10_trending.append(content_info)
        count += 1

# Print out the top 10 trending content items
for i, content in enumerate(top_10_trending, 1):
    print(f'Trending #{i}: {content["title"]} | Rating: {content["rating"]} | Creator: {content["creator"]} | Synopsis: {content["synopsis"]}')
