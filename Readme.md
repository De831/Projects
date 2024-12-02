### README for GitHub Commits

This repository contains a series of scripts and functions that automate various tasks such as domain querying, web scraping, and data processing. Below is an overview of each part of the code:

---

#### **1. Bash Script for DNS Query**
- **File**: `dns_query.sh`
- **Functionality**: 
  - The script takes a domain name as input and performs a DNS query using the `dig` command. It retrieves the IP address of a given domain using a specified DNS server (`10.10.10.26`).
  - If the domain name is not provided as an argument, the script will display a usage message and exit.

  **Usage**:
  ```bash
  ./dns_query.sh <domain_name>
  ```

---

#### **2. Web Scraping with Selenium and Pandas**
- **File**: `scrape_county_surplus_data.py`
- **Functionality**:
  - This Python script uses Selenium WebDriver to scrape surplus funds data from the Polk County Clerk's website (`https://www.polkcountyclerk.net/280/Surplus-Funds-List`).
  - After scraping the data, it structures it into a Pandas DataFrame and saves it as a CSV file (`county_surplus_data.csv`).
  - The script:
    - Waits for the page to load.
    - Extracts relevant data (Sale Date, Tax Deed Number, Certificate Number, etc.).
    - Cleans the data (removes scientific notation for certain columns).
    - Saves the cleaned data to a CSV file.

  **Dependencies**:
  - `selenium`
  - `pandas`
  
  **Run the script**:
  ```bash
  python scrape_county_surplus_data.py
  ```

---

#### **3. Selenium for Web Scraping with Phone Number Extraction**
- **File**: `scrape_phone_numbers.py`
- **Functionality**:
  - This Python script uses Selenium WebDriver to scrape phone numbers associated with previous owners from the **TruePeopleSearch** website.
  - For each owner from the `county_surplus_data.csv` (previously scraped), it searches the TruePeopleSearch website to find their phone number using the name and county or zip code.
  - The phone numbers are then added to the DataFrame and saved as a new CSV file (`county_surplus_data_with_phone_numbers.csv`).
  
  **Dependencies**:
  - `selenium`
  - `pandas`
  - `webdriver_manager`
  
  **Run the script**:
  ```bash
  python scrape_phone_numbers.py
  ```

---

### Key Features
- **Automation**: The scripts automate the process of gathering domain information, scraping data from websites, and extracting specific information like phone numbers.
- **Headless Browsing**: The Selenium-based scripts run in headless mode, which means no browser window is displayed during execution, making it efficient for background tasks.
- **Data Processing**: The scraped data is processed into structured formats (CSV) for further analysis or reporting.

---

### Requirements
- Install Python dependencies:
  ```bash
  pip install selenium pandas webdriver_manager
  ```
- You also need Firefox and GeckoDriver installed on your system.
