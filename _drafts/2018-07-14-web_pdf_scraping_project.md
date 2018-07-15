---
layout: post
published: false
title: Untitled
---
## Web and PDF Scraping Congressional Finance Disclosure Forms 

[Github Repo](https://github.com/opengovernment/readsludge)

Members of Congress are required to publically disclose certain aspects of their finances. This information is made public, but unfortunately is not made accessible in a database. Their websites are freely accessible, as are numerous pdf files with all the required data. But there is no simple way to aggregate this information and look for trends. 

The data can be queried, very slowly, at the links here: 

[House link](http://clerk.house.gov/public_disc/financial-search.aspx)

[Senate link](https://efdsearch.senate.gov/search/home/)

Fortunately, it is possible to scrape the websites using python and selenium. I used this list to find current members of Congress so that I could pull reports for each member of Congress. 

[List of Current Members of Congress](https://theunitedstates.io/congress-legislators/legislators-current.csv

