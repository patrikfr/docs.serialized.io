# Create reaction definition

{% api-method method="post" host="https://api.serialized.io" path="/reactions/definitions" %}
{% api-method-summary %}
Create reaction definition
{% endapi-method-summary %}

{% api-method-description %}
Create a new reaction definition
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="aggregateType" type="string" required=true %}
The aggregate type
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}

{% api-method-parameter name="reactionName" type="string" required=true %}
Unique name of the reaction
{% endapi-method-parameter %}

{% api-method-parameter name="feedName" type="string" required=true %}
Name of the feed
{% endapi-method-parameter %}

{% api-method-parameter name="reactOnEventType" type="string" required=true %}
Event type to react on
{% endapi-method-parameter %}

{% api-method-parameter name="cancelOnEventTypes" type="array" required=false %}
Event types to cancel reaction scheduled in the future
{% endapi-method-parameter %}

{% api-method-parameter name="triggerTimeField" type="string" required=false %}
Path to event data field containing trigger time. If not specified, trigger time will be ASAP. Dot notation supported.
{% endapi-method-parameter %}

{% api-method-parameter name="offset" type="string" required=false %}
Trigger time offset. Defined in the ISO-8601 duration format (PnDTnHnMn.nS). May be negative.
{% endapi-method-parameter %}

{% api-method-parameter name="action" type="object" required=true %}
Action to invoke
{% endapi-method-parameter %}

{% endapi-method-body-parameters %}

{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Events successfully stored.
{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Invalid aggregate type name
{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}
Conflict due to expected version mismatch
{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
Invalid request body
{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -i https://api.serialized.io/aggregates/order/events \
  --header "Content-Type: application/json" \
  --header "Serialized-Access-Key: <YOUR_ACCESS_KEY>" \
  --header "Serialized-Secret-Access-Key: <YOUR_SECRET_ACCESS_KEY>" \
  --data '
{
  "aggregateId": "2c3cf88c-ee88-427e-818a-ab0267511c84",
  "events": [
    {
      "eventId": "f2c8bfc1-c702-4f1a-b295-ef113ed7c8be",
      "eventType": "PaymentProcessed",
      "data": {
        "paymentMethod": "CARD",
        "amount": 1000,
        "currency": "SEK"
      },
      "encryptedData": "string"
    }
  ],
  "expectedVersion": 1
}
'
```
{% endtab %}
{% endtabs %}
