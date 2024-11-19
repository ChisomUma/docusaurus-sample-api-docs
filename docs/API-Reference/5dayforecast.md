---
sidebar_position: 2
---

# 5 Day Forecast
Retrieves weather forecast details for 5 days

## Request URL for API Call

```
GET https://api.openweathermap.org/data/2.5/forecast?zip={zip}&appid=<yourAPIKey>
```

# Query Parameters

| Parameter | Type | Required                                     | Description |
| --------- | ---- | -------------------------------------------- | ----------- |
| zip       | int  | yes |      Zip code for the the desired location       |
| appid          |   int   |       yes                                       |     Unique API Key for authorization        |

## Sample Response
```json
{
    "cod": "200",
    "message": 0,
    "cnt": 40,
    "list": [
        {
            "dt": 1729911600,
            "main": {
                "temp": 295.03,
                "feels_like": 294.19,
                "temp_min": 291.77,
                "temp_max": 295.03,
                "pressure": 1016,
                "sea_level": 1016,
                "grnd_level": 995,
                "humidity": 35,
                "temp_kf": 3.26
            },
            "weather": [
                {
                    "id": 800,
                    "main": "Clear",
                    "description": "clear sky",
                    "icon": "01n"
                }
            ],
            "clouds": {
                "all": 10
            },
            "wind": {
                "speed": 1.28,
                "deg": 304,
                "gust": 2.17
            },
            "visibility": 10000,
            "pop": 0,
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2024-10-26 03:00:00"
        },
}
```

## Response Status Code 

|   Code   |  Description    |
| ---- | ---- | 
| 200 | OK. Current weather successfully retrieved | 