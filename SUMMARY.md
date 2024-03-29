# Table of contents

* [Welcome to Serialized](README.md)

## Basics

* [Accounts](basics/accounts.md)
* [Projects](basics/projects.md)
* [Authentication](basics/authentication.md)
* [Rate limiting](basics/rate-limiting.md)
* [Getting started](basics/getting-started/README.md)
  * [Working with aggregates](basics/getting-started/working-with-aggregates.md)
  * [Projecting events](basics/getting-started/projections.md)
  * [Aggregating events](basics/getting-started/aggregating-events.md)
  * [Reacting to events](basics/getting-started/reacting-to-events.md)
  * [Subscribing to event feeds](basics/getting-started/subscribing-to-event-feeds.md)

## APIS

* [Event Sourcing API](apis/event-sourcing/README.md)
  * [Basic Usage](apis/event-sourcing/basic-usage.md)
  * [Concurrency](apis/event-sourcing/concurrency.md)
  * [Atomicity and Versioning](apis/event-sourcing/atomicity-and-versioning.md)
  * [Deleting Aggregates](apis/event-sourcing/deleting-aggregates.md)
  * [API Reference](apis/event-sourcing/reference/README.md)
    * [Load an Aggregate](apis/event-sourcing/reference/load-all-events-for-an-aggregate.md)
    * [Store Events](apis/event-sourcing/reference/store-events.md)
    * [Check if an aggregate exists](apis/event-sourcing/reference/check-if-an-aggregate-exists.md)
    * [Delete an Aggregate](apis/event-sourcing/reference/delete-an-aggregate.md)
    * [Delete all Aggregates by type](apis/event-sourcing/reference/delete-all-aggregates-by-type.md)
* [Feeds API](apis/feeds/README.md)
  * [Basic Usage](apis/feeds/basic-usage.md)
  * [Sequence Numbers](apis/feeds/sequence-numbers.md)
  * [The \_all feed](apis/feeds/using-the-_all-feed.md)
  * [API Reference](apis/feeds/reference/README.md)
    * [Get feeds overview](apis/feeds/reference/list-feeds.md)
    * [Get feed of events](apis/feeds/reference/get-feed.md)
    * [Get current sequence number](apis/feeds/reference/get-sequence-number.md)
    * [Get events from all feeds](apis/feeds/reference/get-all-feed.md)
    * [Get current global sequence number](apis/feeds/reference/get-global-sequence-number.md)
* [Reactions API](apis/reactions/README.md)
  * [Basic Usage](apis/reactions/basic-usage.md)
  * [Configuring execution time](apis/reactions/configuring-execution-time.md)
  * [API Reference](apis/reactions/reference/README.md)
    * [Create reaction definition](apis/reactions/reference/create-reaction-definition.md)
    * [Get reaction definition](apis/reactions/reference/get-reaction-definition.md)
    * [Update reaction definition](apis/reactions/reference/update-reaction-definition.md)
    * [Delete reaction definition](apis/reactions/reference/delete-reaction-definition.md)
    * [List reaction definitions](apis/reactions/reference/list-reaction-definitions.md)
* [Projections API](apis/projections/README.md)
  * [Basic Usage](apis/projections/basic-usage.md)
  * [JsonPath Functions](apis/projections/event-handlers.md)
  * [Custom Functions](apis/projections/external-projector-functions.md)
  * [Custom Projection IDs](apis/projections/custom-projection-ids.md)
  * [Examples](apis/projections/examples/README.md)
    * [Adding search support to Projections](apis/projections/examples/adding-search-support-to-projections.md)
    * [Aggregating data to a list](apis/projections/examples/aggregating-data-to-a-list.md)
    * [Adding and removing from lists](apis/projections/examples/adding-and-removing-from-lists.md)
  * [API Reference](apis/projections/reference/README.md)
    * [Create Projection Definition](apis/projections/reference/create-projection-definition.md)
    * [Get Projection Definition](apis/projections/reference/get-projection-definition.md)
    * [Update Projection Definition](apis/projections/reference/update-projection-definition.md)
    * [Delete Projection Definition](apis/projections/reference/delete-projection-definition.md)
    * [List Projection Definitions](apis/projections/reference/list-projection-definitions.md)
    * [Get Projections Overview](apis/projections/reference/get-projections-overview.md)
    * [Get Single Projection](apis/projections/reference/get-single-projection.md)
    * [List Single Projections](apis/projections/reference/list-single-projections.md)
    * [Delete/recreate Single Projections](apis/projections/reference/delete-single-projections.md)
    * [Get Aggregated Projection](apis/projections/reference/get-aggregated-projection.md)
    * [Delete/recreate Aggregated Projections](apis/projections/reference/delete-aggregated-projections.md)
* [Tenants API](apis/tenants-api/README.md)
  * [Basic Usage](apis/tenants-api/basic-usage.md)
  * [API Reference](apis/tenants-api/api-reference/README.md)
    * [Add Tenant](apis/tenants-api/api-reference/add-tenant.md)
    * [Delete Tenant](apis/tenants-api/api-reference/delete-tenant.md)

## Client libraries

* [Java client](https://github.com/serialized-io/client-java)
* [Go client \(unofficial\)](https://github.com/marcusolsson/serialized-go)

## Tools

* [Projection Tester](https://console.serialized.io/projection-tester)
* [Swagger API Definition](https://serialized.io/api.json)

## Advanced

* [Multi-Tenancy](advanced/multi-tenant-projects.md)
* [Encrypting Event data](advanced/encrypting-event-data.md)
* [Conditional requests](advanced/conditional-requests.md)
* [Request signatures](advanced/request-signatures.md)

