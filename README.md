## **Project Name:** Web-Scraping-Mini-Project

# Web-Scraping-Mini-Project-Python

A beginner-friendly Python web scraping mini project that fetches and parses the homepage of [tutorialsfreak.com](https://www.tutorialsfreak.com/) using the `requests` and `BeautifulSoup` libraries. This script explores core BeautifulSoup features, including accessing HTML tags, extracting navigable strings, finding elements by class, and retrieving image sources. The code is well-commented and structured to mimic a Jupyter notebook workflow, making it easy to learn and execute.

## Key Features
- Fetches webpage content and checks response status.
- Parses HTML to access tags like `<p>`, `<a>`, `<h1>`, and `<h2>`.
- Extracts text strings and prettifies HTML elements.
- Searches for specific divs by class and lists all image sources.
- Includes ethical notes on respecting `robots.txt` and terms of service.

## How to Run
1. Install dependencies: `pip install requests beautifulsoup4`
2. Save the script as `web_scraping_mini_project.py`.
3. Execute: `python web_scraping_mini_project.py`

## Notes
- This project is for educational purposes only. Ensure compliance with the target website's `robots.txt` and terms of service.
- Feel free to fork and extend this project!


## **Python Code is here**:

```python

## Web Scraping Mini Project: Scraping tutorialsfreak.com
## This script demonstrates basic web scraping using requests and BeautifulSoup.
## It fetches the page, parses HTML, accesses tags/strings, and finds elements.

import requests
from bs4 import BeautifulSoup

## Fetch the webpage
web = requests.get("https://www.tutorialsfreak.com/")
print(web)  ## Expected: <Response [200]>

## Parse the content with BeautifulSoup
soup = BeautifulSoup(web.content, "html.parser")

## Section: Accessing Tags
## Demonstrates how to access specific HTML tags.
tag = soup.html
print(type(tag))  ## Expected: <class 'bs4.element.Tag'>

tag = soup.p
print(tag)  ## First <p> tag

tag = soup.a
print(tag)  ## First <a> tag

tag = soup.h1
print(tag)  ## First <h1> tag

tag = soup.h2
print(tag)  ## First <h2> tag

## Section: Navigable Strings
## Extracts text content from tags.
tag = soup.p.string
print(tag)  ## Text from first <p>

tag = soup.h1.string
print(tag)  ## Text from first <h1>

tag = soup.h2.string
print(tag)  ## Text from first <h2>

## Section: BeautifulSoup Methods
## Explores soup properties and search methods.
print(soup.name)  ## Expected: '[document]'

print(soup.title)  ## <title> tag

print(soup.find('h1'))  ## First <h1>

print(soup.find_all('h1'))  ## All <h1> tags

print(soup.find('p'))  ## First <p>

print(soup.find_all('p'))  ## All <p> tags

## Section: Comments and Prettifying
## Handles strings and formatted HTML output.
com = soup.p.string
print(com)  ## Same as navigable string

print(soup.p.prettify())  ## Prettified <p> tag

## Section: Finding Elements by Class
## Finds a specific div by class (fixed typo in class name).
class_data = soup.find("div", class_="bg-white border-0 p-3 card-footer")
print(class_data)  ## The matching div element

## Extract all image sources
img = soup.find_all('img')
for i in img:
    print(i.get("src"))  ## Prints all image src attributes
