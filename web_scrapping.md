# web scrapping
import requests
from bs4 import BeautifulSoup

# Make a request to the website
url = "https://www.example.com"
page = requests.get(url)

# Parse the HTML content of the page
soup = BeautifulSoup(page.content, "html.parser")

# Find a specific tag, for example a `p` tag
paras = soup.find_all("p")

# Extract the text from the tags
for para in paras:
    print(para.text)
