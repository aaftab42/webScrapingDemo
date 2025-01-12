# Web Scraping Demo

This repository contains a simple Python script to demonstrate web scraping using the BeautifulSoup library. The script extracts book titles and ratings from a sample website.

---

## **Features**
- Scrapes data from multiple pages of a website.
- Extracts book titles and their ratings.
- Stores the data in a Python dictionary.

---

## **How It Works**
1. The script uses the `requests` library to fetch pages from the website.
2. The `BeautifulSoup` library is used to parse HTML and extract data.
3. A loop iterates through all 51 pages, and for each page:
   - It finds all books using the `.product_pod` class.
   - Extracts book titles from the `a` tag.
   - Extracts ratings from the `p` tag and stores them.

---

## **Required Libraries**
To run the script, you need to install the following libraries:

- `requests`: To fetch data from the website.
- `beautifulsoup4`: For parsing the HTML and extracting data.

To install the required libraries, run the following command:
```python
pip install requests beautifulsoup4

## Python Code
import requests
from bs4 import BeautifulSoup

# Base URL for paginated books
page_url = 'https://books.toscrape.com/catalogue/page-{}.html'

# Dictionary to store book titles and their ratings
books = {}

# Loop through all 50 pages (1-50)
for page in range(1, 51):
    print(f'Fetching data from page {page}...')
    
    # Request the HTML content of the current page
    response = requests.get(page_url.format(page))
    
    # Parse the HTML content using BeautifulSoup and the lxml parser
    soup = BeautifulSoup(response.text, 'lxml')
    
    # Select all book containers (each with the class 'product_pod')
    products = soup.select('.product_pod')
    
    # Iterate through each book container
    for product in products:
        # Extract the book title from the 'a' tag (second 'a' tag in the hierarchy)
        title = product.select('a')[1]['title']
        
        # Extract the book rating class (e.g., "One", "Two", etc.)
        rating = product.select('p')[0]['class'][1]
        
        # Add the title and rating to the dictionary
        books[title] = rating

# Output the scraped data
print("\nScraped Book Data:")
for title, rating in books.items():
    print(f'Title: "{title}", Rating: "{rating}"')
```

## **Example Output**
The script outputs the title and rating of each book in the following format:

```vbnet
Fetching data from page 1...
Fetching data from page 2...
...
Scraped Book Data:
Title: "A Light in the Attic", Rating: "Three"
Title: "Tipping the Velvet", Rating: "One"
Title: "Soumission", Rating: "Two"
...
```

## **Note**
- Web scraping is useful for collecting data but always check the website's policy before scraping.
- If scraping is not allowed, your IP may get blocked.
- To avoid detection, consider using tools like Selenium to mimic natural user behavior.
