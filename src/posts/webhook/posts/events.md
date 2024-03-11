---
title: "Events"
summary: "The webhook module gives you the option to use predefined events or create custom events. This guide allows you to create your personalized events in a clear and flexible way, adapting them to the specific format of your system."
eleventyNavigation:
  key: Events
  parent: Webhook
  order: 1
---

## Creating custom events

To leverage our webhook module, you have the option to utilize the events we've pre-defined or craft your own. This guide will walk you through the process of creating custom events, providing you with the flexibility to tailor the functionality according to your specific needs.

To initiate the creation process, effortlessly submit a request to the provided URL along with the following set of data:

```bash
# METHOD - POST

https://wfc.digital/webhook/createCustomEvent
```

<br>

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

<br>

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

<br>

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
