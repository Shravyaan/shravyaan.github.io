---
layout: default
title: 'How to Get Data from the Web with Python (Scraping vs. APIs)'
---

As a developer, you'll often need to get data from the internet. This week, I learned the two main ways to do this in Python: **Web Scraping** and **Using an API with JSON**.

They solve the same problem, but as I learned in my "Python for Everybody" course, they are fundamentally different.

---

## Method 1: Web Scraping 

**The Idea:** Web scraping is for reading a website that was built for **humans**. Your script downloads the raw HTML and "scrapes" it to find the data you want.

**The Tool:** We use `requests` to download the page and `BeautifulSoup` to search the HTML.

**When to use it:** You use this when the website does **not** have an API. The main downside is that if the website's HTML layout changes, your scraper will break.

### Code Example: Web Scraping

Here's a simple script that scrapes a test website to find the title of the first book on the page.

```python
import requests
from bs4 import BeautifulSoup

# Goal: Scrape the title of the first book.

print("--- Starting Web Scrape ---")
# 1. Fetch the HTML content of the page
url_to_scrape = "[http://books.toscrape.com/](http://books.toscrape.com/)"
response = requests.get(url_to_scrape)
html_content = response.text

# 2. "Parse" the HTML with BeautifulSoup
soup = BeautifulSoup(html_content, "html.parser")

# 3. Find the specific tag (I found this by inspecting the page)
first_h3 = soup.find("h3")
first_title_tag = first_h3.find("a")

# 4. Extract the 'title' attribute
title = first_title_tag.get("title")

print(f"The scraped title is: {title}")

Here is the final, complete plan. This is everything you need to do to post your blog.

Step 1: Create Your New Blog Post File
Go to your shravyaan.github.io repository in VS Code.

Go into the _posts folder.

Create a new file with this exact name: 2025-10-27-how-to-get-data-from-the-web-with-python.md

Copy and paste the entire block of text below into that new file.

Markdown

---
layout: default
title: 'How to Get Data from the Web with Python (Scraping vs. APIs)'
---

As a developer, you'll often need to get data from the internet. This week, I learned the two main ways to do this in Python: **Web Scraping** and **Using an API with JSON**.

They solve the same problem, but as I learned in my "Python for Everybody" course, they are fundamentally different.

---

## Method 1: Web Scraping 

**The Idea:** Web scraping is for reading a website that was built for **humans**. Your script downloads the raw HTML and "scrapes" it to find the data you want.

**The Tool:** We use `requests` to download the page and `BeautifulSoup` to search the HTML.

**When to use it:** You use this when the website does **not** have an API. The main downside is that if the website's HTML layout changes, your scraper will break.

### Code Example: Web Scraping

Here's a simple script that scrapes a test website to find the title of the first book on the page.

```python
import requests
from bs4 import BeautifulSoup

# Goal: Scrape the title of the first book.

print("--- Starting Web Scrape ---")
# 1. Fetch the HTML content of the page
url_to_scrape = "[http://books.toscrape.com/](http://books.toscrape.com/)"
response = requests.get(url_to_scrape)
html_content = response.text

# 2. "Parse" the HTML with BeautifulSoup
soup = BeautifulSoup(html_content, "html.parser")

# 3. Find the specific tag (I found this by inspecting the page)
first_h3 = soup.find("h3")
first_title_tag = first_h3.find("a")

# 4. Extract the 'title' attribute
title = first_title_tag.get("title")

print(f"The scraped title is: {title}")
```

## Method 2: Using an API with JSON 
The Idea: An API is a "front door" built for computers. It sends data in a clean, predictable format called JSON.

The Tool: We can use the json library to parse this JSON text into a native Python dictionary or list.

When to use it: Always use an API if one is available. It's reliable, fast, and won't break if the website's visual design changes.

Code Example: Parsing a JSON String
```python
import json

# This is a sample JSON string, like what an API would send.
# It's a list of two user objects.
data = '''
[
  { "id" : "001",
    "x" : "2",
    "name" : "Chuck"
  } ,
  { "id" : "009",
    "x" : "7",
    "name" : "Brent"
  }
]'''

# 1. "Load" the JSON string into a Python list
info = json.loads(data)
print('User count:', len(info))

# 2. Now we can loop through the list and
#    access the data just like a normal Python object!
for item in info:
    print('Name', item['name'])
    print('Id', item['id'])
    print('Attribute', item['x'])
```

Conclusion
Scraping is for reading human-readable pages, while APIs are for getting computer-readable data from a structured source. Learning both this week was a huge step in making my Python scripts truly powerful.
