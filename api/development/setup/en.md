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

### Setting up Redis

We recommend setting up Redis through Docker.

Create a volume for Redis:

```
docker volume create otr-redis
```

Run Redis. Optionally, add `--restart-always` if you don't want to remember to start it up all the time.
```
docker run -d -p 6379:6379 --name otr-redis -v otr-redis:/data redis
```

### Configuring the API

With a fresh PostgreSQL database instance and other required frameworks installed, the API can now be built and configured.

Clone the API and create a config file at `otr-api/API/appsettings.Development.json`. Fill in the values from the [`example.appsettings.json` template](https://github.com/osu-tournament-rating/otr-api/blob/master/API/example.appsettings.json).

#### Connection Strings

- The `ConnectionStrings.DefaultConnection` format is as follows:\
`"Server=<domain>;Port=<port>;User Id=<postgres_user>;Password=<postgres_password>;Include Error Detail=true;"`
> An example connection string for local development would look like:\
`"Server=localhost;Port=5432;User Id=postgres;Password=otrdev;Include Error Detail=true;"`
- `ConnectionStrings.CollectorConnection` is used for reading database diagnostics from another service. For development, there's no need to worry about this. Using a dummy value like `http://localhost` will work fine.
- `ConnectionStrings.RedisConnection` is used for connecting to Redis. The format is picky; Assuming the default port is used for Redis, input `localhost:6379` (no `http://`, etc.) into this field.

#### Osu

Currently the configuration requires both an osu! API v1 key and v2 OAuth2 credentials, however the use of the v1 API will be phased out very soon. When creating the OAuth2 client, the redirect URL is optional. If testing alongside `otr-web`, set the redirect URL to `http://localhost:3000/auth`.

- `Osu.ApiKey`: osu! API v1 key
- `Osu.ClientId`: osu! API v2 client id
- `Osu.ClientSecret`: osu! API v2 client secret
- `Osu.AutoUpdateUsers`: Whether the background workers should update outdated user info (`false` for development is recommended)
- `Osu.AllowDataFetching`: Whether the background workers will look to populate newly added matches from the website.

#### Jwt

- `Jwt.Key` is the secret the API uses to encode and decode JSON Web Tokens. This can be set to any string.
- `Jwt.Audience` refers to the intended recipient of the JWT. This can be set to any string for development purposes, but in production should be the intended resource server, such as `https://some.production.api.url`.

#### Auth

- `Auth.ClientCallbackUrl` is the local route that osu! will redirect users to. This should be set to `http://localhost:3000/auth`. It is only required to be set if the `otr-web` project is also being tested with this API. Your osu! API v2 client must have this URL as a redirect URL.
- `Auth.EnforceWhitelist` decides whether the API should block all incoming requests from users who do not have the `whitelist` [scope](/api/scopes/en.md). We recommend leaving this as `false` in development. It will eventually be removed once o!TR exits private alpha.

#### Rate Limit

-`RateLimit.PermitLimit` is the default number of requests allotted to each authenticated user or client.
- `RateLimit.Window` represents the default ratelimit refresh period in seconds.