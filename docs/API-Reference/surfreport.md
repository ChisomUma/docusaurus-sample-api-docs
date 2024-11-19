# Surfreport
Contains information about surfing conditions, including the surf height, water temperature, wind, and tide. Also provides an overall recommendation about whether to go surfing.

## Endpoint
```
GET surfreport/{beachId}
```
Gets the surf conditions for a specific beach ID.

## Parameters

### Path parameters

| Parameter | Type | Required | Description    |
| --------- | ---- | -------- | --- |
|   beachid        | int     |  yes        |  	The value for the beach you want to look up. Valid `beachId` values are available from our site at `sampleurl.com`.   |

### Query parameters

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| days      | int | Optional    |     The number of days to include in the response. Max is 7. Default is 3.        |
|   time        |   int.  Unix format (ms since 1970) in UTC.  |    Optional      |     If you include the time, then only the current hour will be returned in the response.        |

## Example request
```
curl -I -X GET "https://api.openweathermap.org/data/2.5/surfreport?zip=95050&appid=APIKEY&units=imperial&days=2"
```

In the above code, replace `APIKEY` with your actual API key.

## Example response 
```
{
    "surfreport": [
        {
            "beach": "Santa Cruz",
            "monday": {
                "1pm": {
                    "tide": 5,
                    "wind": 15,
                    "watertemp": 80,
                    "surfheight": 5,
                    "recommendation": "Go surfing!"
                },
                "2pm": {
                    "tide": -1,
                    "wind": 1,
                    "watertemp": 50,
                    "surfheight": 3,
                    "recommendation": "Surfing conditions are okay, not great."
                },
                "3pm": {
                    "tide": -1,
                    "wind": 10,
                    "watertemp": 65,
                    "surfheight": 1,
                    "recommendation": "Not a good day for surfing."
                }
                ...
            }
        }
    ]
}
```

### Response definition
| Response Item               | Description                                                                                                                                                                                                                                                                                  | Data Type |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| beach                       | The beach you selected based on the beach ID in the request. The beach name is the official name as described in the National Park Service Geodatabase.                                                                                                                                     | String    |
| day                       | The day of the week selected. A maximum of 3 days gets returned in the response.                                                                                                                                                                                                            | Object    |
| time                      | The time for the conditions. This item is included only if you include a time parameter in the request.                                                                                                                                                                                     | String    |
| day/time/tide           | The level of tide at the beach for a specific day and time. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point indicates transition.       | Integer   |
| day/time/wind           | The wind speed at the beach, measured in knots (nautical miles per hour). Wind affects the surf height and general wave conditions. Speeds over 15 knots create undesirable surf conditions due to white caps and choppy waters.                                                            | Integer   |
| day/time/watertemp      | The temperature of the water, returned in Fahrenheit or Celsius based on specified units. Water temperatures below 70°F require a wetsuit; below 60°F, a minimum 3mm wetsuit with booties is recommended for warmth.                                                                         | Integer   |
| day/time/surfheight     | The height of the waves, returned in feet or centimeters depending on specified units. A minimum height of 3 feet is needed for surfing. Surf heights over 10 feet are unsafe for surfing.                                                                                                   | Integer   |
| day/time/recommendation | An overall recommendation based on wind, water temperature, and surf height. Possible responses are: (1) "Go surfing!", (2) "Surfing conditions are okay, not great", and (3) "Not a good day for surfing." Scores are combined to form a percentage: 0-59% for response 3, 60-80% for response 2, and 81-100% for response 1. | String    |

