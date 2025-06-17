# Real-Estate-Listings-Data-Pipeline
This project provides a complete data pipeline for analyzing real estate listings from Otodom, leveraging Snowflake, Python, Google Sheets, and Brightdata. The workflow covers data extraction, transformation, enrichment, and analysis to answer key business questions about the Polish real estate market.

Project Structure
Problems_n_Solutions.txt
Snowflake_script_Otodom_Analysis.txt
Address_Title/
    Otodom_Apartment_major_cities_dataset_Address.csv
    Otodom_Apartment_major_cities_dataset_Translate.csv
Datasets/
    Otodom_Apartment_major_cities_dataset_ORG_JSON_Format_Part1.csv
    Otodom_Apartment_major_cities_dataset_ORG_JSON_Format_Part2.csv
    Otodom_Apartment_major_cities_dataset_ORG_JSON_Format_Part3.csv
Python_scripts/
    fetch_address_Otodom_Analysis.py
    load_data_gsheet_to_SF_Otodom_Analysis.py
    ...

Workflow Overview
1. Data Acquisition
Download real estate listings from Otodom via Brightdata.
Export the dataset to a Snowflake stage.
2. Snowflake Setup
Create a Snowflake account and install SnowSQL.
Set up the database, warehouse, and required tables using scripts in Snowflake_script_Otodom_Analysis.txt.
Load the raw JSON or CSV data into Snowflake tables.
3. Data Transformation
Flatten the JSON data into a tabular format (otodom_data_flatten).
Clean and transform fields (e.g., price, surface area, advertiser type).
4. Data Enrichment
Address Enrichment:
Use fetch_address_Otodom_Analysis.py to convert coordinates to addresses, or upload address CSVs from Address_Title.
Title Translation:
Use Google Sheets API or load_data_gsheet_to_SF_Otodom_Analysis.py to translate titles from Polish to English.
5. Data Integration
Join the flattened data, enriched addresses, and translated titles into a final transformed table (OTODOM_DATA_TRANSFORMED).
Add an APARTMENT_FLAG to classify listings.
6. Analysis
Use the transformed data to answer business questions (see Problems_n_Solutions.txt), such as:
Average rental prices by city and apartment size
Most luxurious and affordable neighborhoods
Distribution of private vs. business ads
Key Files
Snowflake_script_Otodom_Analysis.txt:
Contains all Snowflake SQL scripts and step-by-step instructions.
Python_scripts:
Python scripts for address enrichment and Google Sheets integration.
Address_Title:
CSV files for address and title translation (if not using Python).
Problems_n_Solutions.txt:
Contains business questions and their solutions.
Prerequisites
Snowflake account and SnowSQL installed
Python 3.x and required packages (see Python_Prerequisites_Otodom_Analysis.txt)
Google Cloud project with Drive and Sheets API enabled (for translation)
Access to Brightdata for data extraction
Usage
Set up Snowflake:
Run the SQL scripts in Snowflake_script_Otodom_Analysis.txt to create the database, warehouse, and tables.

Load Data:
Export data from Brightdata to your Snowflake stage and load it into the tables.

Transform and Enrich Data:

Run the Python scripts for address and title enrichment, or upload the provided CSVs.
Load the enriched data back into Snowflake.
Run Analyses:
Use the provided SQL queries to answer business questions.
