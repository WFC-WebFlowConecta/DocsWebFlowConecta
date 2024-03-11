---
title: "List Events"
summary: "This subtopic is aimed at how to create your personalized events with information about routes, tokens..."
eleventyNavigation:
  key: List Events
  parent: Webhook
  order: 2
---

To create custom events, you must send the `eventId`. Use this route together with your authentication token to access all events available in your account.

```bash
# METHOD - GET

https://api.wfc.digital/webhook/listEvents?authorization=<your_token_here>
```

<br>

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

<br>

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
