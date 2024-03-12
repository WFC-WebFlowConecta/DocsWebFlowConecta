---
title: "Authentication"
summary: "Here, we will take care of the entire authentication process for our WFC project. This section is dedicated to managing user credentials and generating authentication token."
eleventyNavigation:
  key: Authentication
  parent: Getting Started
  order: 1
---

Here, we will take care of the entire authentication process for our WFC project. This section is dedicated to managing user credentials and generating authentication token.

## Create Account

To create an account, simply send a request to the following route, with the following data.

```bash
# METHOD - POST

https://api.wfc.digital/auth/createAccount
```

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
      <td>email</td>
      <td>string</td>
      <td>Here you send your email</td>
    <tr>
    <tr>
      <td>password</td>
      <td>string</td>
      <td>Here you write your password</td>
    <tr>
    <tr>
      <td>name</td>
      <td>string</td>
      <td>Here you write your name</td>
    <tr>
    <tr>
      <td>nickname</td>
      <td>string</td>
      <td>Here you write your nickname</td>
    <tr>
    </tbody>
  </table>
</div>

<br>

- **Possible returns:**

```json
{
  "default": {
    "statusCode": 201,
    "statusText": "account created successfully",
    "statusType": "success"
  }
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "invalid email format",
    "statusType": "error"
  }
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this email exists in our database",
    "statusType": "error"
  }
}
```

<br>

## Login Account

Upon successful login, you will be issued a credential, specifically an authorization token, delivered directly within the response of your request. Utilize these credentials when accessing routes that mandate authentication by including the token in the route header, formatted as follows: `authorization: Bearer <token>
`

```bash
# METHOD - POST

https://api.wfc.digital/auth/loginAccount
```

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
      <td>email</td>
      <td>string</td>
      <td>Here you send your email</td>
    <tr>
    <tr>
      <td>password</td>
      <td>string</td>
      <td>Here you write your password</td>
    <tr>
    </tbody>
  </table>
</div>

<br>

- **Possible returns:**

```json
{
  "default": {
    "statusCode": 200,
    "statusText": "login successful",
    "statusType": "success"
  },
  "custom": {
    "id": "<user_id>",
    "email": "<user_email>",
    "password": "<user_hash_password>",
    "name": "<user_name>",
    "nickname": "<user_nickname>",
    "plan": "<user_plan>",
    "status": "<user_status>",
    "createdAt": "<user_date_utc_created_acc>"
  },
  "authorization": "<json_web_token_login_expires_in_2h>"
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this password is not correct",
    "statusType": "error"
}
```

```json
{
  "default": {
    "statusCode": 400,
    "statusText": "this email does not exist in our database",
    "statusType": "error"
}
```
