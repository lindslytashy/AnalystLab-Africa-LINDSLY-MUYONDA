# Weather Data ETL Pipeline

AnalystLab Africa — Batch B Internship — Week 7
Author: Lindsly

## Project Overview

This project is a simple ETL pipeline that pulls live weather data from the OpenWeather API for five African cities, cleans it up with Pandas, and stores it for analysis. The goal was to practice the full extract, transform, load process end to end using a real API rather than a static dataset.

## Data Source

I used the OpenWeather Current Weather API (openweathermap.org/api) to pull data for Harare, Lagos, Nairobi, Johannesburg and Accra. For each city I collected the city name, temperature in Celsius and Fahrenheit, feels-like temperature, humidity, weather condition and description, wind speed in both m/s and km/h, and a timestamp.

## ETL Process

The extraction step calls the OpenWeather API once for each city and pulls the relevant fields out of the JSON response into a list of records.

The transformation step loads those records into a Pandas DataFrame, makes sure every column has the right data type, adds a couple of extra columns (Fahrenheit and km/h) to make the data easier to read, and sorts everything by city.

The load step saves the cleaned dataset in two formats: a CSV file and a SQLite database, so it can be reused for future analysis either way.

Finally, the analysis step calculates which city was hottest, coldest, most humid and windiest, and works out the average temperature and humidity across all five cities.

## Tools Used

Python, Pandas, Requests, SQLite (built into Python) and the OpenWeather API.

## Steps Taken

I started by creating a free OpenWeather account and generating an API key. I stored that key as an environment variable rather than hardcoding it into the script, so it wouldn't end up public on GitHub. Then I ran the pipeline script, which handled extraction, transformation, loading and analysis in one go, and reviewed the results it printed out along with the saved files.

## Key Findings

Accra was the hottest city at 25.1°C, while Johannesburg was the coldest at 21.2°C. Lagos had the highest humidity at 92 percent, and Nairobi was the windiest at 14.7 km/h. Across all five cities the average temperature was 23.3°C and the average humidity was 55 percent. Most cities were cloudy at the time of collection, with Johannesburg the only one showing clear skies.

## How to Run

Install the dependencies with pip install -r requirements.txt, set your API key as an environment variable called OPENWEATHER_API_KEY, then run python weather_etl.py.

## Files in this Repo

weather_etl.py is the full pipeline script. requirements.txt lists the Python dependencies. raw_weather_data.csv is the raw extracted data, clean_weather_data.csv is the cleaned dataset, and weather_data.db is the same data stored in SQLite. README.md is this file.