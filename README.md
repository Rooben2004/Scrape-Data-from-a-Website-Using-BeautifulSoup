# Scrape-Data-from-a-Website-Using-BeautifulSoup
Step 1: #import libraries
import requests
from bs4 import BeautifulSoup
import csv
Step 2: #requesting the website
URL = 'https://www.ndtv.com/'
response = requests.get(URL)
print("The response code is : ", response)
Step 3: #parse the HTML document
soup = BeautifulSoup(response.content,'html.parser')
print(soup)
Step 4: #Extract the news headline from HTML
headlines = soup.find_all('h3')
Step 5: #Display the headlines
for headline in headlines:
    print(headline.text,)
Step 6: #saving the headline in a CSV file
with open('headlines.csv', mode='w', newline='',encoding='utf-8') as file:
    writer = csv.writer(file)
    writer.writerow(['headline'])
    for headline in headlines:
        writer.writerow([headline.get_text()])
print("Headlines have been saved to headlines.csv")

