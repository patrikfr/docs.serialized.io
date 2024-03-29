# List Projection Definitions

{% api-method method="get" host="https://api.serialized.io" path="/projections/definitions" %}
{% api-method-summary %}
List projection definitions
{% endapi-method-summary %}

{% api-method-description %}
List all definitions
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Projection definitions successfully received
{% endapi-method-response-example-description %}

```javascript
{
  "definitions": [
    {
      "projectionName": "orders",
      "feedName": "order",
      "handlers": [
        {
          "eventType": "OrderCancelledEvent",
          "functionUri": "https://your-server.com/lambda",
          "functions": [
            {
              "function": "inc",
              "targetSelector": "$.projection.orders[?]",
              "eventSelector": "$.event[?]",
              "targetFilter": "@.orderId == $.event.orderId",
              "eventFilter": "@.orderAmount > 4000"
            }
          ]
        }
      ]
    }
  ]
  "hasMore": false,
  "totalCount": 1
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example

{% tabs %}
{% tab title="cURL" %}
```bash
curl -i \
  --header "Serialized-Access-Key: <YOUR_ACCESS_KEY>" \
  --header "Serialized-Secret-Access-Key: <YOUR_SECRET_ACCESS_KEY>" \
  https://api.serialized.io/projections/definitions
```
{% endtab %}

{% tab title="Java" %}
```java
import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;

Client client = ClientBuilder.newClient();
URI apiRoot = URI.create("https://api.serialized.io");

Map response = client.target(apiRoot)
    .path("projections")
    .path("definitions")
    .request()
    .header("Serialized-Access-Key", "<YOUR_ACCESS_KEY>")
    .header("Serialized-Secret-Access-Key", "<YOUR_SECRET_ACCESS_KEY>")
    .get(Map.class);
```
{% endtab %}

{% tab title="C\#" %}
```csharp
using RestSharp;
using System;

var client = new RestClient("https://api.serialized.io");

var request = new RestRequest("projections/definitions", Method.GET)
   .AddHeader("Serialized-Access-Key", "<YOUR_ACCESS_KEY>")
   .AddHeader("Serialized-Secret-Access-Key", "<YOUR_SECRET_ACCESS_KEY>");

var response = client.Execute<Dictionary<string, Object>>(request);
```
{% endtab %}

{% tab title="Node" %}
```javascript
const axios = require("axios");

const client = axios.create({
  baseURL: "https://api.serialized.io",
  headers: {"Serialized-Access-Key": "<YOUR_ACCESS_KEY>"},
  headers: {"Serialized-Secret-Access-Key": "<YOUR_SECRET_ACCESS_KEY>"}
});

client.get("projections/definitions")
    .then(function (response) {
      // Handle response
    })
    .catch(function (error) {
      // Handle error
    });
```
{% endtab %}
{% endtabs %}

