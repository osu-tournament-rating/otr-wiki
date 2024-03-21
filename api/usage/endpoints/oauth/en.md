# OAuth

### Authorize OAuth Client

Authorize an OAuth client, returning access credentials.

Request\
( **POST** ) `/oauth/token`

Query Parameters\
`clientId` integer\
The id of the OAuth client.

`clientSecret` string\
The secret key assigned to this client.

Example Request
```js
fetch("https://api.otr.stagec.xyz/api/v1/oauth/token?clientId=123&clientSecret=abcdefg", {
  method: "POST",
});
```

Response Format\
Returns [OAuth Response](/api/usage/objects/en.md#oauthresponse)

### Refresh

Refresh an expired `accessToken`.

Request\
( **POST** ) `/oauth/refresh`

Query Parameters\
`refreshToken` string\
The refresh token provided when authorizing.

Example Request
```js
fetch("https://api.otr.stagec.xyz/api/v1/oauth/refresh?refreshToken=abcdefg", {
  method: "POST",
});
```

Response Format\
Returns [OAuthResponse](/api/usage/objects/en.md#oauthresponse), containing a new `accessToken`.

