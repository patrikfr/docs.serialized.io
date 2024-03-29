# Basic Usage

Reactions are configured to react to a specific event and trigger an action whenever that event is processed by the event reactor. An example could be sending a confirmation email to a customer when an order has been successfully placed.

It is not possible for a Reaction to trigger on an event that has happened in the past. Reactions are always configured to listen to events from the moment when the Reaction is configured.

## Actions

Each reaction is configured with a specific Action that defines what will happen when the reaction is triggered. When a Reaction is triggered it will execute its configured Action.

Currently Serialized offer two different pre-defined action types that you can use to integrate with external systems. The specific Slack action and the more generic HTTP action

## HTTP Action

The action type \(`HTTP_POST`\) requires the field `targetUri` to be populated with the address that should receive the POST request. Optionally the field `httpHeaders` can be set, i.e. to handle Basic Authentication etc.

### Receiving reaction requests

The reaction requests are HTTP POST requests with a JSON body. The JSON has the following format:

```javascript
{  
   "metadata":{  
      "aggregateId":"<some-aggregate-id>",
      "timestamp": <epoc-millis>,
      "sequenceNumber": <n>
   },
   "event":{  
      "eventId":"<some-event-id>",
      "eventType":"<event-type>",
      "data":{  
         "key":"value",
         "key":"value",
         ...
      }
   }
}
```

### Securing the external endpoint

As the end-point specified in the `targetUri` must be exposed to the public internet it should be protected. Currently it’s possible to utilize Basic Authentication and include the appropriate HTTP header in the Reaction definition.

```javascript
{
  "reactionName": "notify-on-order-shipped",
  "feedName": "order",
  "reactOnEventType": "OrderShippedEvent",
  "action": {
    "actionType": "HTTP_POST",
    "targetUri": "https://your-service",
    "httpHeaders": {
      "Authorization": "Basic c2VasXlZdyW2dGsONfM5fD4adleRDgVbDNgRkgFgZUpgoxgNHdsg15QktFcm1ndjI="
    }    
  }
}
```

## Slack Action

The action type \(`SLACK_POST`\) requires the field `targetUri` to be populated with a valid [Slack webhook URI](https://api.slack.com/incoming-webhooks). The message text is specified in the field `body`. Simple templating is supported and event data can be accessed using dot \(.\) notation.

Example of a Reaction posting a notification to Slack:

```javascript
{
  "reactionName": "on-order-placed-slack-notifier",
  "feedName": "order",
  "reactOnEventType": "OrderPlacedEvent",
  "action": {
    "actionType": "SLACK_POST",
    "targetUri": "https://hooks.slack.com/services/T0000/B0000/XXXX",
    "body": "A new order with number ${event.data.orderNumber} was placed by ${event.data.customer.email}!"
  }
}
```

Given this event:

```javascript
{
  "eventId": "ca37d05c-a852-4de5-961f-16fb35e8cd7b",
  "eventType": "OrderPlacedEvent",
  "data": {  
    "orderNumber": "12312345",
    "customer": {
      "email": "customer@example.com"
    }
  }
}
```

the message to Slack will look like this:

`A new order with number 12312345 was placed by customer@example.com!`

## Automatic retries

Serialized Reactions have a built-in retry mechanism and will be retried several times over the course of a day. A `2xx` response is required for success, whereas a `4xx` or `5xx` response will be treated as an error and retried.

{% hint style="info" %}
You can see all retries and any errors for your executed reactions in the Serialized Console.
{% endhint %}

