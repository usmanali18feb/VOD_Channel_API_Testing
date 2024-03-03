# DASH VoD Channel API

This API facilitates the creation of a DASH (Dynamic Adaptive Streaming over HTTP) Video on Demand (VoD) channel. It enables you to post a DASH VoD channel with specific parameters.

## Getting Started

### Prerequisites

Before running the tests, make sure you have the following:

- [Node.js](https://nodejs.org/) installed
- [Newman](https://learning.postman.com/docs/collections/using-newman-cli/installing-running-newman/) Installed





- **API key:** Obtain your API key for authentication.
- **MRSS URL:** Provide the MRSS (Media Really Simple Syndication) URL for the DASH content.
- **Channel ID:** Unique identifier for the DASH channel.
- **Delivery Types:** Specify the delivery type; in this case, set it to "dash".
- **Base URL:** The base URL for the API.

### Installation
1. Clone the repository:

    ```bash
    git clone https://github.com/usmanali18feb/VOD_Channel_API_Testing
    ```

2. Install Newman for API testing:
:

    ```bash
    npm install -g newman
    ```

### Running the API

You can use Newman to run this API collection. Ensure that you set the required environment variables before running the collection.

    newman run DASH_VoD_Channel.json -e environment.json


## Usage

### POST DASH VoD Channel
Create a DASH VoD channel by sending a POST request to the specified endpoint.

- **Endpoint:** `{{baseURL}}/ad-aggregation-service/mrss/channel/{{channelId}}`
- **Method:** POST

#### Headers:
- `api-key: {{api-key}}`
- `Content-Type: application/json`

#### Body:

```json
{
  "url": "{{MRSS-url}}",
  "deliverytypes": ["{{deliverytypes}}"]
}
```

#### Response:
The API response will contain information about the DASH VoD channel, including the DASH URL and clip details.

## Tests
The following tests are performed after the API response:

- Check the status code and ensure it is 200.
- Validate that the response is in JSON format.
- Verify the existence of the 'dash' property in the response body.
- Check the 'url' property in the 'dash' property:
  - Ensure it is not null.
  - Confirm that it contains the expected substring.
- Verify the existence of the 'clips' property in the 'dash' property:
  - Ensure it is an array.
  - Confirm it has at least one item.
- Check the properties of the first item in the 'clips' array.

## Variables
- **api-key:** Your API key for authentication.
- **MRSS-url:** MRSS URL for the DASH content.
- **channelId:** Unique identifier for the DASH channel.
- **deliverytypes:** Delivery type, set to "dash".
- **baseURL:** Base URL for the API.
