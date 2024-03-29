# Get current global sequence number

{% api-method method="head" host="https://api.serialized.io" path="/feeds/\_all" %}
{% api-method-summary %}
Get current global sequence number
{% endapi-method-summary %}

{% api-method-description %}
Get current global sequence number at head for all feeds. Note that since this is a **HEAD** request the value is returned as a HTTP header \(`Serialized-SequenceNumber-Current`\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Serialized-Access-Key" type="string" required=true %}
Access key for the project
{% endapi-method-parameter %}

{% api-method-parameter name="Serialized-Secret-Access-Key" type="string" required=true %}
Secret access key for the project
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Global sequence number successfully retrieved
{% endapi-method-response-example-description %}

```text
HTTP/1.1 200 OK
Serialized-SequenceNumber-Current: 23
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -I \
  --header "Serialized-Access-Key: <YOUR_ACCESS_KEY>" \
  --header "Serialized-Secret-Access-Key: <YOUR_SECRET_ACCESS_KEY>" \
  https://api.serialized.io/feeds/_all
```
{% endtab %}

{% tab title="Java" %}
```java
import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.core.Response;

Client client = ClientBuilder.newClient();
URI apiRoot = URI.create("https://api.serialized.io");

Response response = client.target(apiRoot)
    .path("feeds")
    .path("_all")
    .request()
    .header("Serialized-Access-Key", "<YOUR_ACCESS_KEY>")
    .header("Serialized-Secret-Access-Key", "<YOUR_SECRET_ACCESS_KEY>")
    .head();

String globalSequenceNumber = (String) response.getHeaders()
    .getFirst("Serialized-SequenceNumber-Current");

```
{% endtab %}

{% tab title="C\#" %}
```csharp
using RestSharp;
using System;

var client = new RestClient("https://api.serialized.io");

var request = new RestRequest("feeds/_all")
   .AddHeader("Serialized-Access-Key", "<YOUR_ACCESS_KEY>")
   .AddHeader("Serialized-Secret-Access-Key", "<YOUR_SECRET_ACCESS_KEY>");

var aggregateResponse = client.Head(request);
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

client.head("feeds/_all")
    .then(function (response) {
      // Handle response
    })
    .catch(function (error) {
      // Handle error
    });

```
{% endtab %}
{% endtabs %}

