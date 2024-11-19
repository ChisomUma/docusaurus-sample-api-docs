---
sidebar_position: 1
---

# Current Weather Data 
Gets the current weather for 95050 in `imperial units`.

## Request URL for API Call
```
GET https://api.openweathermap.org/data/2.5/weather?zip={zip}&units={uinits}&appid=<yourAPIKey>
```

## Query Parameters 

| Parameter | Type | Required | Description    |
| --------- | ---- | -------- | --- |
|   zip        | int     |  yes        |  Zip code for the the desired location   |
| units          |   string   |     yes     |  Units of meaurements. `standard`, `metric` and `imperial` units are available.  |
| appid      | int | yes     |  Unique API Key for authorization  |


## Sample Response 
```json
{
    "coord": {
        "lon": -121.953,
        "lat": 37.3492
    },
    "weather": [
        {
            "id": 711,
            "main": "Smoke",
            "description": "smoke",
            "icon": "50d"
        }
    ],
}
```

## Response Status Code 

|   Code   |  Description    |
| ---- | ---- | 
| 200 | OK. Current weather successfully retrieved | 
