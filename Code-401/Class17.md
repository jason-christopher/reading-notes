# Web Scraping

Web scraping is a technique to automatically access and extract large amounts of information from a website, which can save a huge amount of time and effort.

Important notes about web scraping:

* Read through the website’s Terms and Conditions to understand how you can legally use the data. Most sites prohibit you from using the data for commercial purposes.
* Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.

## Python Code

We start by importing the following libraries:

* `import requests` (`pip install requests`)
* `i`mport urllib.request` (?)
* `from bs4 import BeautifulSoup` (`pip install beautifulsoup4`)

Next, we set the url to the website and access the site with our requests library.

```
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
soup = BeautifulSoup(response.text, “html.parser”)
```

Then use the methods like `.findAll` to locate the desired elements.

Source: <https://towardsdatascience.com/how-to-web-scrape-with-python-in-4-minutes-bc49186a8460>

## Web Scraping best practices to follow to scrape without getting blocked

* Respect Robots.txt
* Make the crawling slower, do not slam the server, treat websites nicely
* Do not follow the same crawling pattern
* Make requests through Proxies and rotate them as needed
* Rotate User Agents and corresponding HTTP Request Headers between requests
* Use a headless browser like Puppeteer, Selenium or Playwright
* Beware of Honey Pot Traps
* Check if Website is Changing Layouts
* Avoid scraping data behind a login
* Use Captcha Solving Services
* How can websites detect web scraping?
* How do you find out if a website has blocked or banned you?

Source: <https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/>

## Things I want to know more about

* Getting around Captcha
