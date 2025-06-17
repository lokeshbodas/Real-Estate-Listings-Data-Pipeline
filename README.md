# Real-Estate-Listings-Data-Pipeline
This project provides a complete data pipeline for analyzing real estate listings from Otodom using Snowflake, Python, Google Sheets, and Brightdata.

Project Structure
Snowflake_script_Otodom_Analysis.txt: Main Snowflake SQL scripts and step-by-step instructions.
Problems_n_Solutions.txt: Analytical questions and their solutions.
Address_Title/: Contains CSVs for address and translated titles.
Datasets/: Original dataset CSVs.
Python_scripts/: Python scripts for data fetching, transformation, and integration with Google Sheets.
End-to-End Flow
1. Data Acquisition
Download real estate data from Otodom via Brightdata.
Export the dataset to a Snowflake stage.
2. Snowflake Setup
Create Database & Warehouse:
Set up a Snowflake database and virtual warehouse.
Create Tables:
otodom_data_dump: Raw JSON data.
otodom_data_flatten: Flattened data table.
OTODOM_DATA_FLATTEN_ADDRESS_FULL: Address data.
OTODOM_DATA_FLATTEN_TRANSLATE_FULL: Translated titles.
OTODOM_DATA_TRANSFORMED: Final transformed dataset.
3. Data Loading & Transformation
Load Data:
Use Snowflake stages and file formats to load JSON/CSV data into tables.
Flatten JSON:
Extract fields from JSON and flatten into columns.
Clean Data:
Remove test or null records.
4. Address & Title Enrichment
Address Resolution:
Use the Python script fetch_address.py or upload the provided CSV (Address_Title/Otodom_Apartment_major_cities_dataset_Address.csv) to populate address data.
Title Translation:
Use Google Sheets API via the Python script or upload the translated CSV (Address_Title/Otodom_Apartment_major_cities_dataset_Translate.csv).
5. Data Integration
Join the flattened data, address, and translated titles into the final transformed table (OTODOM_DATA_TRANSFORMED).
Add derived columns such as apartment_flag for property type classification.
6. Analysis
Use the final table to answer business questions (see Problems_n_Solutions.txt), such as:
Average rental prices by room count and city.
Most affordable neighborhoods.
Distribution of private ads.
Python Scripts
fetch_address.py: Fetches address information using geolocation.
load_data_gsheet_to_SF.py: Loads translated titles from Google Sheets to Snowflake.
See Python_Prerequisites_Otodom_Analysis.txt for required Python packages.
Loading Data to Snowflake
Use PUT and COPY INTO commands to load CSVs into Snowflake tables.
See detailed steps in Snowflake_script_Otodom_Analysis.txt.
Prerequisites
Snowflake account and SnowSQL CLI.
Python 3.x with required packages.
Google Cloud project with Drive and Sheets API enabled (for translation).
