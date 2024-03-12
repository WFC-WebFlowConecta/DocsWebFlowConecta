---
title: "Access Hook"
summary: "In this topic you will learn how to send data to your hook, and thus fully use our webhook module."
eleventyNavigation:
  key: Access Hook
  parent: Webhook
  order: 4
---

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

## Data processing

The handling of key values within the payload remains unaltered, allowing for enhanced flexibility for users implementing our webhook module. This means that any characteristics, such as white `spaces within` a value or `special characters`, are transmitted to the redirect link exactly as they are in their raw form.

- **Possible returns:**

The Access Hook does not adhere to a standardized return format. Since it operates as a redirect route, both the return status and the content of the response are replicated from the result of the request initiated in the redirection link.
