---
title: "Hooks"
summary: "In this subtopic we will talk about how to create and start hooks."
eleventyNavigation:
  key: Hooks
  parent: Webhook
  order: 2
---

## Create Hooks

Creating hooks is essential for utilizing webhooks with event semantics. To initiate a hook, effortlessly submit a request to the provided link with the following data.

```bash
# METHOD - POST

https://api.wfc.digital/webhook/createHook
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

## Access Hook

An access hook involves utilizing hooks in conjunction with custom or predefined events. It functions by initiating a request to a specified URL X, and subsequently redirecting the `request` from that point onward.

Each hook generated in the preceding session through the `Create Hook` operation possesses a unique identifier. This identifier serves the purpose of distinguishing one hook from another and is crucial in the context of access, specifying the particular hook to which data is directed for redirection.

To transmit data to your hook, you can effortlessly do so by sending the data to the corresponding URL, with the `hookId` included as route parameters:

```bash
# METHOD - POST

https://api.wfc.digital/webhook/accessHook/:hookId
```

- **Params:**

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
      <td>hookId</td>
      <td>string</td>
      <td>Id of the hook whose data you want to send</td>
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
      <td>payload</td>
      <td>json</td>
      <td>This field designates the destination for the data transmission. The specific data to be sent varies according to the hook type. In the `createHook` operation, the `fields` field is defined as a string array. These fields represent the required payload elements that must be included when sending the data</td>
    </tr>
    </tbody>
  </table>
</div>

- **Possible returns:**

The Access Hook does not adhere to a standardized return format. Since it operates as a redirect route, both the return status and the content of the response are replicated from the result of the request initiated in the redirection link.

## Data processing in access hook

The handling of key values within the payload remains unaltered, allowing for enhanced flexibility for users implementing our webhook module. This means that any characteristics, such as white `spaces within` a value or `special characters`, are transmitted to the redirect link exactly as they are in their raw form.
