# Home Assistant Sportmonks API Integration

## Overview

This repository contains instructions for integrating the Sportmonks API with Home Assistant to display the Premier League table.

## Step 1: Obtain API Key

1. Go to the [Sportmonks website](https://www.sportmonks.com/) and sign up for an account.
2. After creating an account, obtain your API key from the Sportmonks dashboard.

## Step 2: Configure Home Assistant

1. Open your Home Assistant configuration file (`configuration.yaml`).
2. Add the following configuration under the `sensor` section to fetch data from the Sportmonks API.

```
sensor:
  - platform: rest
    name: Premier League Table
    resource: https://soccer.sportmonks.com/api/v2.0/leagues/{LEAGUE_ID}/standings?api_token=YOUR_API_KEY
    method: GET
    value_template: "{{ value_json.data }}"
    scan_interval: 3600
```


Replace {LEAGUE_ID} with the ID of the Premier League from the Sportmonks API (you can find it in the documentation or through API calls).

Replace YOUR_API_KEY with the API key you obtained from Sportmonks.

## Step 3: Display the League Table
Now that you have configured the API integration, you can display the league table in your Home Assistant frontend or Lovelace UI.
Edit your Lovelace UI configuration to add a new card to display the league table. For example, you can use the "Entities" card

```
views:
  - title: My Dashboard
    cards:
      - type: entities
        entities:
          - entity: sensor.premier_league_table
        title: Premier League Table
```


## Step 4: Restart Home Assistant
After making changes to the configuration, save the file and restart Home Assistant for the changes to take effect.
Usage
Now, when you access your Home Assistant frontend, you should see the "Premier League Table" card displaying the league standings.

Please note that the actual implementation might require adjustments based on the specific data structure and requirements of the Sportmonks API. Always refer to the official documentation of both Home Assistant and the Sportmonks API for the most accurate and up-to-date information.

Remember to keep your API key secure and avoid sharing it publicly. If you are using version control for your Home Assistant configuration, consider using secrets to protect your API key.
