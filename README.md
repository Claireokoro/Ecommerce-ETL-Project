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

### Scraping Single Page
The provided code demonstrates how to scrape book titles, prices, ratings, availability, and images from a single page of the online bookstore.

### Scraping Entire Site
The code snippets illustrate the process of scraping data from multiple pages of the bookstore using a loop and collecting information into lists.

## Data Transformation
### Rating Mapping
Mapping text ratings ('One', 'Two', 'Three', 'Four', 'Five') to numerical values (1, 2, 3, 4, 5) for better analysis.

### Data Cleaning
Cleaning the scraped data, converting price to a float, and preparing it for analysis.

## Data Loading
Saving the transformed data into a CSV file named 'Books.csv'.

## PowerBI Visualization
Utilizing Microsoft PowerBI to visualize the scraped and cleaned data, showcasing book-related insights. The visualization highlights top and bottom books by price, average ratings, total number of books, average price, and books by rating.

## Repository Structure
```
├── notebooks/
│   ├── Web_Scraping_Notebook.ipynb
│   └── PowerBI_Dashboard.ipynb
├── data/
│   └── Books.csv
├── Bookstore_Scraping_PowerBI.pbix
└── README.md
```

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
