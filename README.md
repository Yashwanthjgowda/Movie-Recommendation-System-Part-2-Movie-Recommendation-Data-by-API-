## Movie Recommendation System - Fetching Data via API

This documentation provides a detailed explanation of using Python to interact with the IMDb API to fetch movie data based on a cast name. The fetched data is converted into a DataFrame for further analysis or processing. The script demonstrates the use of the http.client library for making HTTPS requests and the pandas library for handling data.

## Prerequisites

## IMDb API Access: You need access to the IMDb API through RapidAPI.

## RapidAPI Key: Ensure you have a valid RapidAPI key.

## Python Libraries: Install the required libraries:

## http.client: Standard library for HTTP requests.

## sl: For secure HTTPS connections.

## json: To handle JSON responses.

## pandas: For data manipulation (install using pip install pandas).

# Script Description

Code

import http.client
import ssl
import json
import pandas as pd

# Create HTTPS connection
conn = http.client.HTTPSConnection(
    "imdb_api4.p.rapidapi.com",
    context=ssl._create_unverified_context()
)

# Set headers
headers = {
    'x-rapidapi-key': "YOUR_RAPIDAPI_KEY_HERE",
    'x-rapidapi-host': "imdb_api4.p.rapidapi.com"
}

# Send request
conn.request("GET", "/get_movies_by_cast_name", headers=headers)

# Get response
res = conn.getresponse()
data = res.read()

# Decode response
json_data = json.loads(data.decode("utf-8"))

# Convert JSON to DataFrame
df = pd.DataFrame(json_data)

# Print DataFrame
print(df)

Steps

# Establish HTTPS Connection:

An HTTPSConnection object is created using the IMDb API's host and a secure SSL context.

# Set API Headers:

The x-rapidapi-key and x-rapidapi-host headers are used for authentication.

# Send GET Request:

A GET request is sent to the endpoint /get_movies_by_cast_name to fetch movie data.

# Handle API Response:

The response is read and decoded into JSON format using json.loads().

# Convert JSON to DataFrame:

The JSON data is converted to a Pandas DataFrame for easier handling and analysis.

# Print DataFrame:

The DataFrame is printed to display the fetched movie data.

# Usage

# Replace API Key:

Replace the placeholder RapidAPI key (YOUR_RAPIDAPI_KEY_HERE) with your valid API key.

# Run the Script:

Execute the script in your Python environment.

# Analyze Data:

Use the DataFrame (df) to analyze or manipulate the movie data as needed.

# Notes

The ssl._create_unverified_context() is used here to bypass SSL verification. Use this cautiously in a production environment.

Ensure your API key is kept secure and not hardcoded in scripts shared publicly.

## Dependencies

Python 3.x

Pandas library (pip install pandas)

## License

This script is for educational and personal use. The data fetched from the IMDb API is subject to IMDb's terms of use.

Acknowledgments

IMDb API provided by RapidAPI.

Python community for the libraries used in this script.

