# Election-Analysis


This project involves extracting, analyzing, and organizing statewise election results data from the Election Commission of India (ECI) website.
The goal is to compile detailed insights into parliamentary constituency outcomes across various states, focusing on party-wise performance, winning candidates, and key electoral statistics. The information is organized into envelopes by state and party, working with complete investigation and reportage on political decision patterns and political elements.


## Table of Contents

- [Installation](#installation)
- [Data Extraction](#data-extraction)
- [Organizing CSV Files by State](#organizing-csv-files-by-state)
- [Key Insights](#key-insights)
- [References](#references)


## Installation

1. Clone the repository:

   ```bash
   https://github.com/Atharv1610/Election-Analysis.git
   cd Election-Analysis
	```
2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

## Data Extraction
The Election-Analysis project begins by scraping comprehensive statewise election results data from the Election Commission of India (ECI) website. Using Python's requests and BeautifulSoup libraries, URLs are parsed to access detailed parliamentary constituency outcomes.
 ```bash
import requests
from bs4 import BeautifulSoup
import os

url = 'https://results.eci.gov.in/PcResultGenJune2024/index.htm'

response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')
   ```


## Organizing CSV Files by State
The election data collected from the Election Commission of India (ECI) website is organized into a structured folder hierarchy. Each state registry inside the 'state' envelope contains subfolders addressing individual ideological groups. Inside each party organizer, CSV documents exemplify itemized parliamentary electorate results, including characteristics, for example, seat number, parliament supporters, winning applicant, all out votes, and edge. This systematic arrangement ensures efficient data retrieval and comprehensive analysis of statewise election outcomes, facilitating detailed insights into electoral trends and political dynamics across India.

 ```bash
import requests
from bs4 import BeautifulSoup
import pandas as pds
def fetch_data(url):
    response = requests.get(url)
    if response.status_code == 200:
        return response.content
    else:
        print(f"Failed to retrieve {url}")
        return None

state_party_links = {}

for state_name, url in state_links.items():
    print(f"Fetching party links for {state_name} from {url}")
    
    page_content = fetch_data(url)
    if page_content:
        soup = BeautifulSoup(page_content, 'html.parser')
        
        party_rows = soup.select('tbody tr.tr')
        
        party_list = []

        for row in party_rows:
            party_name = row.find('td', style='text-align:left').text.strip()
            party_link = row.find('a')['href']
            party_list.append((party_name, party_link))

        state_party_links[state_name] = party_list
    
    print(f"Party links fetched for {state_name}")
    print("-" * 50)

print("State Party Links:")
for state, parties in state_party_links.items():
    print(f"State: {state}")
    for party_name, party_link in parties:
        print(f"Party Name: {party_name}, Link: {party_link}")
    print("-" * 50)
```

## Key Insights
1. Voter Turnout:
	
 	The 2024 Indian parliamentary elections showcased a significant average voter turnout of 65% across constituencies, underscoring diverse levels of civic engagement and political participation nationwide.


2. Margin of Victory (MoV):


	The Margin of Victory (MoV) in the 2024 Indian parliamentary elections serves as a crucial indicator of electoral competitiveness and party performance. With the Bharatiya Janata Party (BJP) securing an 
        average MoV of 192,809.77 votes, MoV data provides deep insights into the electoral dynamics and strategic implications for political parties. It highlights varying levels of voter support across 
        different constituencies, revealing where parties have strong incumbency advantages or face closely contested races.

![image](https://github.com/Atharv1610/Election-Analysis/assets/103433059/a2fadedb-1360-4e8f-b54a-145c4ae2bf7a)


3. Emerging Trends and Regional Insights:

   	The elections highlighted stark differences in voter priorities between urban and rural constituencies. Urban areas, grappling with issues like 
        infrastructure development, employment opportunities, and governance efficiency, showed distinct voting patterns compared to rural areas, which 
        prioritized agricultural welfare, local development projects, and traditional community concerns.Identity politics and localized issues played a pivotal 
         role in shaping electoral outcomes. Various regions exhibited polarization driven by local sentiments, cultural identities, and historical contexts. 
         Regional parties and alliances strategically leveraged these factors to consolidate support, impacting the distribution of seats and electoral alliances.


## References
	https://results.eci.gov.in/
  	https://results.eci.gov.in/PcResultGenJune2024/index.htm


