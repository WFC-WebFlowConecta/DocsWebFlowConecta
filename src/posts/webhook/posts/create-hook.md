---
title: "Create Hook"
summary: "In this subtopic we will talk about how to create and start hooks."
eleventyNavigation:
  key: Create Hook
  parent: Webhook
  order: 3
---

Creating hooks is essential for utilizing webhooks with event semantics. To initiate a hook, effortlessly submit a request to the provided link with the following data.

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
      <td>eventId</td>
      <td>string</td>
      <td>ID of the event you want to use (check your events in the topic *List events*)</td>
    </tr>
    <tr>
      <td>nameHook</td>
      <td>string</td>
      <td>Submit the name you want to name your event</td>
    </tr>
    <tr>
      <td>typeRequest</td>
      <td>"get" | "post"</td>
      <td>Type of request that will be sent to the `redirect` link</td>
    </tr>
    <tr>
      <td>redirect</td>
      <td>string</td>
      <td>Redirect link</td>
    </tr>
    <tr>
      <td>filds</td>
      <td>string[]</td>
      <td>Fields that your request will have, being sent in the body or query params of the request</td>
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
    "statusText": "hook created successfully",
    "statusType": "success"
  }
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this event id does not correspond to any event",
    "statusType": "error"
  }
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this event does not belong to your account",
    "statusType": "error"
  }
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this url is not valid",
    "statusType": "error"
  }
}
```
