# Home Assistant Sportmonks API Integration

## Overview

This repository contains instructions for integrating the Sportmonks API with Home Assistant to display the Premier League table.

## Step 1: Obtain API Key

1. Go to the [Sportmonks website](https://www.sportmonks.com/) and sign up for an account.
2. After creating an account, obtain your API key from the Sportmonks dashboard.

## Step 2: Configure Home Assistant

1. Open your Home Assistant configuration file (`configuration.yaml`).
2. Add the following configuration under the `sensor` section to fetch data from the Sportmonks API.

```yaml
sensor:
  - platform: rest
    name: Premier League Table
    resource: https://soccer.sportmonks.com/api/v2.0/leagues/{LEAGUE_ID}/standings?api_token=YOUR_API_KEY
    method: GET
    value_template: "{{ value_json.data }}"
    scan_interval: 3600
