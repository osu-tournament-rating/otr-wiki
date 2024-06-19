# o!TR API Setup

This document serves as a guide on how to setup a local development environment for the o!TR API.

## Required Dependencies

The following dependencies are required to be installed for building the API.

- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

## Setup

### Install Entity Framework

```
dotnet tool install --global dotnet-ef
```

### Setting up a PostgreSQL Database

Follow [this guide](/api/maintenance/database/en.md) to setup your local database. Make sure this docker container is always running before you launch the API.

### Configuring the API

With a fresh PostgreSQL database instance and other required frameworks installed, the API can now be built and configured.

Clone the API and create a config file at `otr-api/API/appsettings.Development.json`. Fill in the values from the `example.appsettings.json` template.

#### Rate Limit

The `PermitLimit` field is the default number of requests allotted to each authenticated user or client.

The `Window` field represents the default ratelimit refresh period (in seconds).

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Trace",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "ConnectionStrings": {
    "DefaultConnection": ""
  },
  "Osu": {
    "ApiKey": "",
    "ClientId": "",
    "ClientSecret": "",
    "AutoUpdateUsers": false,
    "AllowDataFetching": false
  },
  "Jwt": {
    "Key": "",
    "Audience": ""
  },
  "Auth": {
    "ClientCallbackUrl": ""
  },
  "RateLimit": {
    "PermitLimit": 30,
    "Window": 60
  }
}
```

#### Connection String

The connection string format is as follows:\
`"Server=<domain>;Port=<port>;User Id=<postgres_user>;Password=<postgres_password>;Include Error Detail=true;"`

An example connection string for local development would look like:\
`"Server=localhost;Port=5432;User Id=postgres;Password=otrdev;Include Error Detail=true;"`

#### Osu

In order to use any osu! API features, you will need to create an [osu!](https://osu.ppy.sh/) account. You may manage your osu! API clients on your [account settings page](https://osu.ppy.sh/home/account/edit#oauth).

Currently, the configuration requires both an osu! API v1 key and v2 OAuth credentials, however the use of the v1 API will be phased out very soon. When creating the OAuth2 client on osu!'s website, the redirect URL is optional. If testing with `otr-web`, set the redirect URL to `http://localhost:3000/auth`.

#### Jwt

The `Key` field is the secret the API uses to encode and decode JSON Web Tokens. This can be set to any string.

The `Audience` field refers to the intended recipient of the JWT. This can be set to any string for development purposes, but in production should be the intended resource server, such as `https://some.production.api.url`.
