import os

# Define project details
project_name = "SEO-Blog-Post-Creation-Tool"
base_path = f"/mnt/data/{project_name}"
os.makedirs(base_path, exist_ok=True)

# File contents
files = {
    "README.md": """#  SEO Blog Post Creation Tool

An AI-based automation tool that scrapes trending products from e-commerce sites, performs SEO keyword research, generates blog content, and publishes it to WordPress.

---

## Features

- Scrapes best-selling products using BeautifulSoup or Scrapy
- Automates SEO keyword research using Google Keyword Planner or Ubersuggest API
- Generates 150–200 word blog posts using NLP
- Publishes content to WordPress using REST API

---

## Pipeline Overview

1. **Product Scraping**
2. **SEO Keyword Research**
3. **Blog Post Generation**
4. **Content Publishing**

---

##  Example Code

###  Product Scraper (`product_scraper.py`)
```python
import requests
from bs4 import BeautifulSoup

url = "https://www.amazon.com/Best-Sellers/zgbs"
headers = {"User-Agent": "Mozilla/5.0"}
response = requests.get(url, headers=headers)
soup = BeautifulSoup(response.content, 'html.parser')

products = []
for product in soup.find_all('div', {'class': 'zg-item'}):
    name = product.find('a').text.strip()
    link = product.find('a')['href']
    products.append((name, link))

KEYWORDS RESEARCH :
import requests

api_key = "YOUR_API_KEY"
keyword = "product name"
location = "US"

url = "https://api.example.com/keyword-ideas"
response = requests.post(
    url,
    headers={"Authorization": f"Bearer {api_key}"},
    json={"query": keyword, "location": location}
)
keywords = [idea['keyword'] for idea in response.json().get('results', [])]

BLOG  GENERATOR :
def generate_blog_post(product_name, keywords):
    content = (
        f"{product_name} is one of the most trending products online. "
        f"It stands out due to its {keywords[0]} and {keywords[1]} features. "
        f"Perfect for {keywords[2]}, this product delivers excellent value."
    )
    return content

WORDPRESS PUBLISHER:
import requests

api_url = "https://example.com/wp-json/wp/v2/posts"
username = "your_username"
password = "your_password"

def publish_to_wordpress(title, content):
    post_data = {
        "title": title,
        "content": content,
        "status": "publish"
    }
    response = requests.post(api_url, auth=(username, password), json=post_data)
    return response.json().get("link")

PROJECT STRUCTURE :
SEO-Blog-Post-Creation-Tool/
├── product_scraper.py
├── keyword_research.py
├── blog_generator.py
├── content_publisher.py
├── requirements.txt
├── report.md
└── README.md



