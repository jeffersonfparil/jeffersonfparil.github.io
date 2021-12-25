# Weed Wide Web Scraping

[2020-05-18]

This is a simple demonstration of web scraping using [python3](https://www.python.org/downloads/), [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), and [selenium](https://selenium-python.readthedocs.io/installation.html) on Ubuntu 18.04 with the additional pre-requisite of installing [geckodriver](https://github.com/mozilla/geckodriver) for selenium to interact with webpages. Additionally using your favorite web browser's "Inspect Element" and "View Source" functionalities is a must to pin point exactly the html element you want to extract and manipulate.

Import the functions for parsing the web pages:
```
from bs4 import BeautifulSoup
from urllib.request import urlopen as uReq
```
Import the web automation module specifically including the common keys (i.e. for pressing "Enter" in our case):
```
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
```
Import the time module for delaying the execution within the for-loop below to give time for the page to load:
```
import time
```
Import python3's base module for reading and writing csv files:
```
import csv
```
Define the website we want to scrape data from:
```
url = "http://www.weedscience.org/Summary/Herbicide.aspx"
```
Download the webpage and parse:
```
aspx = uReq(url)
soup = BeautifulSoup(aspx.read(), "html.parser")
```
Extract the list of keys we want to enter into one of the webpage's input:
```
herbi_list = [soup.findAll('div', {'class': 'rcbSlide'})[1].findAll('li', {'class': 'rcbItem'})[i].text for i in range(1,len(soup.findAll('div', {'class': 'rcbSlide'})[1].findAll('li', {'class': 'rcbItem'})))]
```
Instantiate our webdriver:
```
driver = webdriver.Firefox()
driver.get(url)
```
Parse, extract the data we need, and save as csv files:
```
for herbi in herbi_list:
    # herbi = 'B (ALS inhibitors)'
    print(herbi)
    input_element = driver.find_element_by_name('ctl00$AboveSideMenu$cmbxHerbicideGroup')
    input_element.clear()
    input_element.send_keys(herbi)
    input_element.send_keys(Keys.ENTER)
    ### wait for the page to load
    time.sleep(20) # we could do better by checking if the key, i.e. herbi variable have been set
    soup = BeautifulSoup(driver.page_source, "html.parser")
    table = soup.find('table', {'id': 'ctl00_Main_RadGrid1_ctl00'}).findAll('tbody')[1]
    OUT = []
    for row in table.findAll('tr'):
        out = []
        for cell in row.select('td'):
            out.append(cell.text.replace("\n", ""))
        OUT.append(out)
    with open("Scrapping_output_" + herbi.replace(" ", "_") + ".csv", "w") as f:
        w = csv.writer(f)
        w.writerows(OUT)
driver.close()
```

## Output
- A (ACCase inhibitors)
- B (ALS inhibitors)
- C1 (Photosystem II inhibitors)
- C2 (PSII inhibitor (Ureas and amides))
- C3 (PSII inhibitors (Nitriles))
- D (PSI Electron Diverter)
- E (PPO inhibitors)
- F1 (Carotenoid biosynthesis inhibitors)
- F2 (HPPD inhibitors)
- F3 (Carotenoid biosynthesis (unknown target))
- F4 (DOXP inhibitors)
- G (EPSP synthase inhibitors)
- H (Glutamine synthase inhibitors)
- I (DHP synthase inhibitors)
- K1 (Microtubule inhibitors)
- K2 (Mitosis inhibitors)
- K3 (Long chain fatty acid inhibitors)
- L (Cellulose inhibitors)
- M (Uncouplers)
- N (Lipid Inhibitors)
- O (Synthetic Auxins)
- P (Auxin transport inhibitors)
- Z (Antimicrotubule mitotic disrupter)
- Z (Cell elongation inhibitors)
- Z (Nucleic acid inhibitors)
- Z (Unknown)