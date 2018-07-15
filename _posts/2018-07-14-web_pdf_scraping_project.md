---
layout: post
published: false
title: 2018-07-14-web_pdf_scraping_project.md
---
## Web and PDF Scraping Congressional Finance Disclosure Forms 

[Github Repo](https://github.com/opengovernment/readsludge)

Members of Congress are required to publically disclose certain aspects of their finances. This information is made public, but unfortunately is not made accessible in a database. Their websites are freely accessible, as are numerous pdf files with all the required data. But there is no simple way to aggregate this information and look for trends. 

The data can be queried, very slowly, at the links here: 

[House link](http://clerk.house.gov/public_disc/financial-search.aspx)

[Senate link](https://efdsearch.senate.gov/search/home/)

Fortunately, it is possible to scrape the websites using python and selenium. I used this list to find current members of Congress so that I could pull reports for each member of Congress. 

[List of Current Members of Congress](https://theunitedstates.io/congress-legislators/legislators-current.csv)

#### Disclaimer

As this was one of my first large-scale projects, a few mistakes were made. I repeat code at times, as I was unable to get functions to return the proper values. I likely append or concatenate some pandas dataframes inefficiently. Refactoring is certainly needed here, but was not done due to time constraints. The main priority was to write code that worked and would produce results. The House and Senate websites are organized quite differently, so it was necessary to create seperate codes for each. 

#### Important Info for Senate Data

I tackled the Senate data first. The site requires that the user select a checkbox indicating thhat they understand the prohibitions on using this data. I chose to use Selenium to automate this process. Once past this hurdle, there are a number of fields that can be queried. I took the Senate data from theunitedstates.io repo, checked off 'Current Senator' and selected 'Annual' and 'Periodic Transactions'. For this project, we are seeking to find data the is reported once a year (the Annual reports) and the periodic updates. Most of the PDFs that are returned are electronically filed machine-generated and machine-readable (that is, I am able to parse the text and values), however some documents are scanned and contain handwriting. I chose to leave these alone as out of scope, but they can be parsed using OCR libraries at a later date. It seems that most documents are filed electronically, fortunately.  

The output is organized into four reports; assets, liabilities, PTR A and PTR B data. The assets.csv file will have reports for all Senators that were parsed at this time. Ideally, we will store these data into respective SQL tables, so that one Senator can be queried easily and we can view all of their assets, liabilities and other financial information in one go. 

senate_stocks.py is the main code. The csv files are the output of the data. Time range of the queries is 

- senate_stocks.py 
- assets.csv
- liab.csv
- ptra.csv
- ptrb.csv

#### Important Notes regarding Senate python code

- I ignored anything with 'paper' in the url, as these will require OCR to parse. 
- Electronically filed reports are essentially just html documents that can be parsed with the usual methods. In my case I used regular expressions and beautifulsoup. 
- was necessary to run selenium in headless browser in order to run this script in cloud 
- was necessary to use wait.until functions to make selenium wait for elements to load properly before attempting to click. time.sleep works as well, and was used when needed. 
Like: `wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, xxx))).click()`
- The code creates a list of links to respective Senator reports. Then the code goes through each link, extracts text and values, and outputs to the various CSV files per relevant table. 
- Start date for report querying is January 1, 2017, written exactly as '01/01/2017'. End date is blank. 


#### Important Info for House Data

Due to time constraints, I was unable to write a working script to repeat the Senate data extraction process for the members of the House of Representatives. I was able to create a script to generate a list of links to reports but will have to leave the text and value extraction to others. I have an incomplete script which I will make available to my predecessor, and am using pdfplumber to parse the pdfs. I was able to get 'raw' text extracted, but it will need a considerable amount of work to organize into tidy data. 

#### Important Notes regarding House python code

- Incomplete 
- Data from pdfs is captured in string format, but still needs to be parsed further. I estimate another 5-10 hours for all data fields. 
- Failed to handle character encoding issues with Reps names. Accents on 'é', for instance, are not working correctly and this causes the query to fail. 
- I included some code to email the results to my email address. This will need to be updated for the proper addresses and ported to the Senate code as well.  











