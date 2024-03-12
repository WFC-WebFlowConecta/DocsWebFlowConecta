---
title: "Events"
summary: "Events are the semantic way to separate hooks."
eleventyNavigation:
  key: Events
  parent: Webhook
  order: 1
---

## Creating Custom Events

To leverage our webhook module, you have the option to utilize the events we've pre-defined or craft your own. This guide will walk you through the process of creating custom events, providing you with the flexibility to tailor the functionality according to your specific needs.

To initiate the creation process, effortlessly submit a request to the provided URL along with the following set of data:

```bash
# METHOD - POST

https://api.wfc.digital/webhook/createCustomEvent
```

- **Headers:**

<div class="table-responsive">
  <table class="table table--striped table--hover">
    <thead>
      <tr>
        <th>Variable</th>
        <th>Type</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
    <tr>
      <td>authorization</td>
      <td>string</td>
      <td>Authorization token generated at user login (expired every two hours)</td>
    </tr>
    </tbody>
  </table>
</div>

- **Body:**

<div class="table-responsive">
  <table class="table table--striped table--hover">
    <thead>
      <tr>
        <th>Variable</th>
        <th>Type</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
    <tr>
      <td>nameEvent</td>
      <td>string</td>
      <td>Custom event name</td>
    </tr>
     <tr>
      <td>description</td>
      <td>string</td>
      <td>Description for the custom event</td>
    </tr>
    </tbody>
  </table>
</div>

- **Possible returns:**

```json
{
  "default": {
    "statusCode": 201,
    "statusText": "customEvent created successfully",
    "statusType": "success"
  },
  "custom": {
    "dataCustomEvent": {
      "userId": "<user_id>",
      "name": "<event_name>",
      "description": "<event_description>",
      "status": true,
      "createdAt": "<created_at_date>"
    }
  }
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this name exist in other custom event",
    "statusType": "error"
  }
}
```

## List Events

To create custom events, you must send the `eventId`. Use this route together with your authentication token to access all events available in your account.

```bash
# METHOD - GET

https://api.wfc.digital/webhook/listEvents?authorization=<your_token_here>
```

- **QueryParams:**

<div class="table-responsive">
  <table class="table table--striped table--hover">
    <thead>
      <tr>
        <th>Variable</th>
        <th>Type</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
    <tr>
      <td>authorization</td>
      <td>string</td>
      <td>Authorization token generated at user login (expired every two hours)</td>
    </tr>
    </tbody>
  </table>
</div>

- **Possible returns:**

```json
{
  "default": {
    "statusCode": 200,
    "statusText": "showing all events available to you",
    "statusType": "success"
  },
  "custom": {
    "availableEvents": [
      {
        "id": "<id_event>",
        "name": "<name_event>",
        "description": "<description_event>",
        "status": "<status_event>",
        "createdAt": "<created_at_date_event>"
      }
    ]
  }
}
```
