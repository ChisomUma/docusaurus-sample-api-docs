---
sidebar_position: 2
---

# Authentication
The weather API uses an API Key, which can be accessed on the [OpenWeatherMap website](https://openweathermap.org/). Click the Signin/Signup button on the top right part of the website navbar and create an account. 

After signing up, you get an API key sent to your email. You can also find the key when you log back into the website by clicking on the API Keys tab. Ensure to keep your API key safe and easy to find.

:::note

The API key becomes active for use after a few hours of reciept.

:::

## API Key Usage 
API request are authenticated using the `Bearer Auth scheme`. To authenticate a request, include your API key in the `Authorization` header of your `HTTP` request. For example:

```
Authorization: Bearer <your_api_key>
```

Authentication can also be carried out as a query parameter in your request URL using your API Key. 