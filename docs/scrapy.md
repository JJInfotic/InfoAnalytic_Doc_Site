# Scrapy Tutorial

## Creating a project[](https://scrapy2.readthedocs.io/en/latest/intro/tutorial.html#creating-a-project "Permalink to this headline")

`scrapy startproject <project name>`

- `scrapy.cfg`: the project configuration file
- `tutorial/`: the project’s python module, you’ll later import your code from here.
- `tutorial/items.py`: the project’s items file.
- `tutorial/pipelines.py`: the project’s pipelines file.
- `tutorial/settings.py`: the project’s settings file.
- `tutorial/spiders/`: a directory where you’ll later put your spiders.

## Defining our Item[](https://scrapy2.readthedocs.io/en/latest/intro/tutorial.html#defining-our-item "Permalink to this headline")

```py
import scrapy

class DmozItem(scrapy.Item):
    title = scrapy.Field()
    link = scrapy.Field()
    desc = scrapy.Field()
```

## Our first Spider[](https://scrapy2.readthedocs.io/en/latest/intro/tutorial.html#our-first-spider "Permalink to this headline")

- [`name`](https://scrapy2.readthedocs.io/en/latest/topics/spiders.html#scrapy.spider.Spider.name "scrapy.spider.Spider.name"): identifies the Spider. It must be unique, that is, you can’t set the same name for different Spiders.
    
- [`start_urls`](https://scrapy2.readthedocs.io/en/latest/topics/spiders.html#scrapy.spider.Spider.start_urls "scrapy.spider.Spider.start_urls"): is a list of URLs where the Spider will begin to crawl from. So, the first pages downloaded will be those listed here. The subsequent URLs will be generated successively from data contained in the start URLs.
    
- [`parse()`](https://scrapy2.readthedocs.io/en/latest/topics/spiders.html#scrapy.spider.Spider.parse "scrapy.spider.Spider.parse") is a method of the spider, which will be called with the downloaded [`Response`](https://scrapy2.readthedocs.io/en/latest/topics/request-response.html#scrapy.http.Response "scrapy.http.Response") object of each start URL. The response is passed to the method as the first and only argument.
    
    This method is responsible for parsing the response data and extracting scraped data (as scraped items) and more URLs to follow.
    
    The [`parse()`](https://scrapy2.readthedocs.io/en/latest/topics/spiders.html#scrapy.spider.Spider.parse "scrapy.spider.Spider.parse") method is in charge of processing the response and returning scraped data (as [`Item`](https://scrapy2.readthedocs.io/en/latest/topics/items.html#scrapy.item.Item "scrapy.item.Item") objects) and more URLs to follow (as [`Request`](https://scrapy2.readthedocs.io/en/latest/topics/request-response.html#scrapy.http.Request "scrapy.http.Request") objects).



```py
#demo_spider.py

import scrapy

class DmozSpider(scrapy.Spider):
    name = "dmoz"
    allowed_domains = ["dmoz.org"]
    start_urls = [
        "http://www.dmoz.org/Computers/Programming/Languages/Python/Books/",
        "http://www.dmoz.org/Computers/Programming/Languages/Python/Resources/"
    ]

    def parse(self, response):
        filename = response.url.split("/")[-2]
        with open(filename, 'wb') as f:
            f.write(response.body)
```

### Crawling[](https://scrapy2.readthedocs.io/en/latest/intro/tutorial.html#crawling "Permalink to this headline")

`scrapy crawl dmoz`

