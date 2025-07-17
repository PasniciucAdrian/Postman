# Postman Project – API Collections

This repository contains three distinct API collections, developed and tested using Postman. Each collection is organized in a separate folder and includes JSON files, request documentation, and relevant screenshots.

## Project Structure

### 1. Weather API
This collection includes multiple GET requests for retrieving weather information using the OpenWeather API. Each request is documented and supported with test result screenshots.

### 2. Open Weather Map
This collection expands the weather-related requests using a free OpenWeather API key. It includes:
- current weather by city name
- weather by geographic coordinates
- multi-day forecast

### 3. Postman-Trello
This collection contains API requests to interact with the Trello platform. Covered operations include:
- fetching board and list details
- creating and deleting cards
- updating card information
- retrieving all cards from specific lists

Each request includes:
- a markdown file with a description
- screenshots of test results
- a `.postman_collection.json` file for direct import into Postman

## Purpose of the Project

This repository is part of a learning process focused on:
- working with REST APIs in Postman
- structuring and testing various request types
- documenting request-response flows
- using authentication keys and dynamic parameters

## How to Use the Collections

1. Clone the repository:
```bash
git clone https://github.com/PasniciucAdrian/Postman.git
```

2. Open Postman.

3. Import the `.postman_collection.json` files from each folder (`Weather API`, `Postman-Trello`, `Open Weather Map`).

4. Use the `README.md` files and screenshots as reference documentation.
