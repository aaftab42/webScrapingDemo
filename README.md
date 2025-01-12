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
```bash
pip install requests beautifulsoup4
