# Authorization Flow

We offer a way for third-party clients to access our API via the OAuth2 standard. Currently, the API is not open for public use. Access will be rolled out in a limited fashion at first before granting broad public usage.

In order to use our API, you must familiarize yourself with our [usage limits](/api/usage/limits/en.md), else risk being suspended from accessing our API.

## Requirements
- `clientId` - The id of your API client
- `clientSecret` - The secret phrase assigned to your client.

## Generate Credentials

Generate access credentials for your client by calling the [/oauth/token](/api/usage/endpoints/oauth/en.md#authorize-oauth-client) endpoint.

## Refresh

When your API `accessToken` expires, you will need to refresh it using the `refreshToken`. See [/oauth/refresh](/api/usage/endpoints/oauth/en.md#refresh)

## Authorization

Always use the `accessToken` parameter in your `Authorization` header as such.

Header: `Authorization`
Value: `Bearer <accessToken>`