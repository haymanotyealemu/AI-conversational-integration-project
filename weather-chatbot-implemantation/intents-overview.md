### Intent: Weather by Geographic Coordinates

📌 Description

This intent handles user queries requesting weather information based on geographic coordinates (latitude and longitude).

Instead of relying on city names, the chatbot extracts numerical parameters representing:

 - Latitude (first number)

 - Longitude (second number)

### Intent Configuration

Intent Name:
 - weather_forecast

Sample Training Phrases

 - Weather at 33.7490 -84.3880

 - What is the weather at 40.7128 -74.0060?

 - Get weather for 34.0522 -118.2437

 - Weather at latitude 41.8781 longitude -87.6298

 - Show forecast at 29.7604 -95.3698

  Parameters Extracted
  
  | Parameter Name | Description                     | Example Value |
| -------------- | ------------------------------- | ------------- |
| latitude       | Geographic latitude coordinate  | 33.7490       |
| longitude      | Geographic longitude coordinate | -84.3880      |

### Entity Design

The intent uses:

 - @sys.number entity for capturing numeric coordinate values

 - Required parameters enabled for both latitude and longitude

 - Parameter prompts configured if values are missing

Example prompt:

Please provide both latitude and longitude values.

### Fulfillment Configuration

 Webhook-Based Response Handling

The Weather_By_Coordinates intent is configured to use Webhook Fulfillment instead of static text responses.

When the intent is matched:

 - Dialogflow extracts the parameters:

    - latitude

     - longitude

 - The intent triggers a Webhook call to a backend service (implemented using Dialogflow Inline Editor – Node.js environment).

 - The extracted parameters are sent in the request payload to the webhook.

 - The webhook processes the request and dynamically constructs a response.

 - The response is returned to Dialogflow and delivered to the user.

