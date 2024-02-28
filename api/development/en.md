# Development

This document serves as a guide on how to setup a local development environment for the o!TR API.

## Required Dependencies

The following dependencies are required to be installed for building the API.

- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- [Entity Framework Core 8](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore)

## Setup

### Setting up a PostgreSQL Database

The API requires a connection to a PostgreSQL database in order to function. The easiest way to accomplish this is through a [Docker](https://www.docker.com/) container.

```sh
# Pull the latest PostgreSQL image
docker pull postgres

# Create and run a container
docker run -d -p 5432:5432 --name otr-postgres-dev -e POSTGRES_PASSWORD=<some_password> postgres
```

### Using the o!TR Demo Database

*Note: The o!TR Demo Database is not available to the public at this time. This document will be updated once we have a public resource.*

```sh
# Copy the SQL file to the container
docker cp demodb.sql <container_name_or_id>:/demodb.sql

# Execute the SQL file with psql
docker exec -it <container_name_or_id> psql -U postgres -d postgres -f /demodb.sql
```

### Configuring the API

With a fresh PostgreSQL database instance and other required frameworks installed, the API can now be built and configured.

Clone the API and create a config file at `otr-api/API/appsettings.Development.json`. Fill in the values from the `example.appsettings.json` template.

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
    "WebLoginAuthSecret": "",
    "PrivilegedClientSecret": "",
    "ClientCallbackUrl": ""
  }
}
```

#### ConnectionStrings

The connection string format is as follows:\
`"Server=<domain>;Port=<port>;User Id=<postgres_user>;Password=<postgres_password>;Include Error Detail=true;"`

An example connection string for local development would look like:\
`"Server=localhost;Port=5432;User Id=postgres;Password=otrdev;Include Error Detail=true;"`

#### Osu

Currently the configuration requires both an osu! API v1 key and v2 OAuth2 credentials, however the use of the v1 API will be phased out very soon. When creating the OAuth2 client, the redirect URL is optional. If testing alongside `otr-web`, set the redirect URL to `http://localhost:3000/auth`.

#### Jwt

The `Key` field is the secret the API uses to encode and decode JSON Web Tokens. This can be set to any string.

The `Audience` field refers to the intended recipient of the JWT. This can be set to any string for development purposes, but in production should be the intended resource server, such as `https://some.production.api.url`.
