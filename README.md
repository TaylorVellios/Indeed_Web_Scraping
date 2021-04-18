# Web Scraping Indeed and LinkedIn for Recent Job Postings
Scraping Indeed (as ethically as possible) for Job Data Across Many Cities For the Younger Nomadic Workforce.


## Purpose
To compile job listing data across the US's largest cities for your career of choice.<br></br>

Millenials and Zoomers are proving that they are happy to move where the jobs are.<br></br>

This script allows the user to gain the following insights:
* Which metropolitan areas in the US have higher concentrations of recent job postings for their industry.
* The companies that post listings in those areas, allowing for an easier job search.
* Locations of employers in the nearby-surrounding cities across the area, allowing the user to see and narrow down housing location choices.


## Dependencies 
#### Indeed_WebScraping.py
* Requests
  ~~~~
  $ pip install requests
  ~~~~
* Pandas
  ~~~~
  $ pip install pandas
  ~~~~
* BeautifulSoup
  ~~~~
  $ pip install beautifulsoup4
  ~~~~
* geopy
  ~~~~
  $ pip install geopy
  ~~~~

### Plotting_Indeed_Data.ipynb
* gmaps
  ~~~~
  $ conda install -c conda-forge gmaps
  ~~~~
* gmaps.config.py file with your api key set to a variable named 'g_key'

<br></br>
## Features
This repository contains a main script (JobData_WebScraper.py) as well as a Jupyter Notebook file (Plotting_Job_Data.ipynb).<br></br>

The included .csv file (CityData_Clean.csv) contains the top 100 cities in the US sorted by descending population size.<br></br>


This python script is made to search and store only recent job postings on Indeed.com (within 30 days) and return them as a .csv file on your machine.<br></br>

### Instructions for Scraper:
* Run JobData_WebScraper.py in bash/terminal

![start](https://user-images.githubusercontent.com/14188580/115120316-82887080-9f72-11eb-8b2d-9c420387291e.PNG)

* Take note of the DataFrame printed - You will be using a single list index or slice notation for the cities you want to search.
* You will be prompted for two inputs:
  1. A Single Index or a One/Two Digit Slice (with colon separator) of the City/State Columns in the DataFrame displayed.
  2. A search term for whatever job title you would like to scrape.

![inputs](https://user-images.githubusercontent.com/14188580/115120324-887e5180-9f72-11eb-95e3-e4b99ded82e4.PNG)

<br></br>

*Please note that this script is set to ping indeed and linkedin once every 30 seconds.*<br>
*By default, this script will search for 8 pages of results per city and filter out anything posted over a month ago.*<br>
### *tl:dr -- IT TAKES A LONG TIME, DO NOT ADJUST SLEEP DURATION*<br>
*Indeed.com will require a captcha if you ping it too often, breaking the program. Leave this open in an active terminal.*
<br></br>
![outputDF](https://user-images.githubusercontent.com/14188580/114607521-43041080-9c62-11eb-95d3-0de4f5f9ee02.PNG)
<br><br>

### Instructions for Mapper:
* Ensure you have set your gmaps api token to a variable named "g_key" in a file named "g_config.py" in this repo's directory.
* Open Plotting_Job_Data.ipynb in Jupyter Notebook.
* Find your output .csv file in the new 'Job_Data' directory created when the scraper finished. It will be named with the current day and your search term.
* Enter the file name of that .csv in the first empty-string variable 'file_name' in the second cell.

![pyter](https://user-images.githubusercontent.com/14188580/114608636-827f2c80-9c63-11eb-8acf-073e63f80182.PNG)

* Run it and see where the jobs pop up!

![default_map](https://user-images.githubusercontent.com/14188580/115132139-2bf75280-9fc3-11eb-955c-b150abe2c4e3.PNG)<br></br>
![zoom_map](https://user-images.githubusercontent.com/14188580/115132140-30237000-9fc3-11eb-9abd-ad2eee3d5df7.PNG)




<br></br>
#### Current Known Issues
4.17.2021<br>
- my python 3.7.3 environment does not work with geopy, this program was written on 3.9.2
- There is no cross-checking between indeed job postings and linkedin
- many job postings provide a useless location such as "greater GENERAL_CITY_NAME metropolitan area", these are filtered down and functional with geopy but the data is not as useful. At this time, cannot narrow location search by employer, too many discrepancies for geopy to handle.

