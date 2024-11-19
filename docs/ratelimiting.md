---
sidebar_position: 3
---

# Rate Limits

To maintain fair usage and safeguard against overuse, the OpenWeatherMap API imposes rate limits on requests, outlined as follows:

* 40 requests per minute per API key
* 5,000 requests per day per API key

## Managing Rate Limits
When rate limits are exceeded, the API replies with an HTTP status code `429` meaninig you have exceeded the number of allowed requests. This response includes headers that show when you are allowed to retry, as in the example below:

| Header Name               | Description                                                               |
| ------------------------- | --------------------------------------------------------------------- |
| X-RateLimit-Limit: 40     | Maximum amount fof requests you can make in current rate limit window. |
| X-RateLimit-Remaining: 0 | The number of requests you have remaining.                             |
| X-RateLimit-Reset: 5634614600                          |       The timestamp, when the current rate limit window will reset.                                                                |


X-RateLimit-Reset offers the Unix timestamp indicating when the rate limit resets, signaling when you can proceed with new requests.

Exceeding the rate limit will throw an error, as shown below:

```
HTTP/2 429
X-RateLimit-Limit: 40
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 5634614600

 {
    "error": {
        "code": 429
        "message": "API rate limit exceeded. Please try again in 60 seconds"
    }
 }
```
