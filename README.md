# VIN Recognition/Decoder Documentation

## Introduction

**VIN (Vehicle Identification Number) Recognition and Decoding API** is a tool designed to extract a VIN from an image that could be of various sources such as ID cards, labels, receipts, invoices, documents, barcodes, etc. This API utilizes advanced image recognition technology to accurately identify and decode the VIN from the image.

Once the VIN has been extracted, the API can then be used to decode the VIN and retrieve important information such as the manufacturer, model, year, country of origin, etc. This information is vital for a range of applications including automobile sales, insurance, and maintenance.

The VIN Recognition and Decoding API is a convenient and efficient solution for organizations and individuals in need of quick and accurate VIN information. It eliminates the need for manual data entry and reduces the risk of human error. The API is easy to integrate into existing systems and can be accessed through a simple API call.

It is important to note that the VIN recognition and decoding process may be impacted by factors such as image quality, resolution, and angle. To ensure the best possible results, it is recommended to use high-quality images and ensure the VIN is clearly visible in the image.

And of course, we added more option, such as method to introduce only the vin as a text and get all the information of the vehicle.

## Authentication

The URL you need to use is the following: `https://vin-recognition-decoder.p.rapidapi.com/`
The API requires the headers listed below:

- **`x-rapidapi-host`**: `vin-recognition-decoder.p.rapidapi.com`
- **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/vin-recognition-decoder/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

## Endpoints

Below are the available endpoints with their descriptions and required parameters.

### 1. **`GET /get-vin2`**

- **Description**: Retrieves VIN decoded info.

| Parameter | Type   | Default | Description                                 | Required |
|-----------|--------|---------|---------------------------------------------|----------|
| `vin`     | string | -       | The VIN to decode                           | Yes      |

Example request:

```javascript
fetch('https://vin-recognition-decoder.p.rapidapi.com/get-vin2?vin=1NXBR32E77Z923602', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'vin-recognition-decoder.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "validate": true,
  "manufacturer": "NUMMI USA",
  "serialNumber": "923602",
  "country": "United States",
  "securityCode": "7",
  "assemblyPlant": "Z",
  "logoImage": "",
  "year": 2007,
  "posibleYear": [
    2007
  ],
  "details": "BR32E",
  "decode": {
    "manufacturer": "NUMMI USA",
    "country": "United States",
    "year": 2007,
    "posibleYear": [
      2007
    ],
    "logoImage": ""
  },
  "decode_all_info": {
    "manufacturer": "NUMMI USA",
    "country": "United States",
    "year": 2007,
    "posibleYear": [
      2007
    ],
    "serialNumber": "923602",
    ...
```

### 2. **`GET /`**

- **Description**: Retrieves information of a vin such as country of origin, model, year, model, car seats, etc.

| Parameter | Type   | Default | Description                            | Required |
|-----------|--------|---------|----------------------------------------|----------|
| `vin`     | string | -       | The VIN code                           | Yes      |

Example request:

```javascript
fetch('https://vin-recognition-decoder.p.rapidapi.com/get-vin?vin=19UYA42601A019296', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'vin-recognition-decoder.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json

```

### 3. **`POST /`**

- **Description**: Retrieves Crypto Metrics.

Example request:

```javascript
fetch('', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'vin-recognition-decoder.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json

```

## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |
