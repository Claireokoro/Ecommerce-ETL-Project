# OnlineBookstore-ETL-Project

---

## Table of Contents
- [Introduction](#introduction)
- [Web Scraping](#web-scraping)
  - [Importing Libraries](#importing-libraries)
  - [Scraping Single Page](#scraping-single-page)
  - [Scraping Entire Site](#scraping-entire-site)
- [Data Transformation](#data-transformation)
  - [Rating Mapping](#rating-mapping)
  - [Data Cleaning](#data-cleaning)
- [Data Loading](#data-loading)
- [PowerBI Visualization](#powerbi-visualization)
- [Repository Structure](#repository-structure)
- [Usage](#usage)
- [Contributions](#contributions)

---
 
## Introduction
This repository showcases a web scraping project involving the extraction of book-related data from an online bookstore using Python libraries like `requests`, `BeautifulSoup`, and `pandas`. The scraped data was then transformed, cleaned, and loaded into a CSV file for further analysis. The extracted dataset was later visualized using Microsoft PowerBI to create an insightful dashboard.

## Web Scraping
### Importing Libraries
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
```

Sure, here's the code for the sections you provided:

## Scraping Single Page
To begin the web scraping process, I utilized the BeautifulSoup library to extract book titles, prices, ratings, availability, and images from a single page of the online bookstore.

```python
# Import necessary libraries
import requests
from bs4 import BeautifulSoup
import pandas as pd

# Define the URL to scrape
url = 'http://books.toscrape.com/catalogue/page-1.html'

# Send a request to the URL and parse the response with BeautifulSoup
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Initialize empty lists to store scraped data
titles = []
prices = []
ratings = []
availability = []
images = []

# Extract data using BeautifulSoup
for h3 in soup.find_all('h3'):
    titles.append(h3.a.attrs['title'])
    
for price in soup.find_all('p', 'price_color'):
    prices.append(price.text)
    
for rating in soup.find_all('p', 'star-rating'):
    ratings.append(rating.attrs['class'][1])
    
for stock in soup.find_all('p', 'instock availability'):
    availability.append(stock.text.strip())
    
for img in soup.find_all('img'):
    images.append(img.attrs['src'].replace('..', 'http://books.toscrape.com'))
```

## Scraping Entire Site
Building upon the single-page scraping, I implemented a loop to scrape data from multiple pages of the online bookstore. This allowed me to collect a comprehensive dataset.

```python
# Define the number of pages to scrape
num_of_pages = 50

# Initialize an empty list to store URLs
urls = []

# Generate URLs for each page
for i in range(1, num_of_pages + 1):
    urls.append(f'http://books.toscrape.com/catalogue/page-{i}.html')

# Loop through each URL and extract data
for url in urls:
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')
    
    # Utilize the extract_data function to collect data
    extract_data(soup)
```

## Data Transformation
After successfully scraping the required data from the online bookstore, the next step involved transforming and preparing the scraped data for analysis. This process included converting and cleaning the data to ensure its suitability for further insights.

### Rating Mapping
The ratings of books were originally in text format (e.g., 'One', 'Two', 'Three', 'Four', 'Five'). To facilitate analysis, these ratings were mapped to numerical values (1, 2, 3, 4, 5).

```python
# Mapping text ratings to numerical values
rating_mapping = {'One': 1, 'Two': 2, 'Three': 3, 'Four': 4, 'Five': 5}
df['Rating'] = df['Rating'].replace(rating_mapping)
```

### Data Cleaning
Several cleaning steps were taken to ensure the data's accuracy and consistency. One crucial step involved converting the 'Price' column to a float by removing any currency symbols.

```python
# Removing currency sign and converting 'Price' to float
df['Price'] = df['Price'].str.replace('Â£', '').astype(float)
```

## Data Saving
Once the data was transformed and cleaned, it was saved into a CSV file named 'Books.csv' for future analysis and visualization.

```python
# Saving the transformed data into a CSV file
df.to_csv('Books.csv', index=False)
```

## PowerBI Visualization
Utilizing Microsoft PowerBI to visualize the scraped and cleaned data, showcasing book-related insights. The visualization highlights top and bottom books by price, average ratings, total number of books, average price, and books by rating.


## Usage
1. Run the provided web scraping code in `Web_Scraping_Notebook.ipynb` to extract data.
2. Transform and clean the extracted data as shown in the notebook.
3. Load the cleaned data into `Books.csv`.
4. Open `PowerBI_Dashboard.ipynb` to visualize the data using PowerBI.

## Contributions
- Izundu Dan-Ekeh
- Okoro Maryclaire Orobosa



---

Feel free to modify and enhance the repository description and structure as needed. The provided structure and content are designed to provide a clear and organized overview of the project's process and outcomes.
