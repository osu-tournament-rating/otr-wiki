# Development

This document will serve as a guide on how to setup a local development environment for the o!TR API.

## Required Dependencies

The following are required to be installed for building the API.

- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- [Entity Framework Core 8](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore)

## Setup

### Setting up a PostgreSQL Container

The API requires a PostgreSQL setup to store the database. The easiest way to acomplish this is through [Docker](https://www.docker.com/). Be sure to fill in the relevant fields denoted {VAR}.

```sh
# Pull the latest PostgreSQL image
docker pull postgres

# Create and run a container
docker run --name {CONTAINER_NAME} -e POSTGRES_PASSWORD {PASSWORD} -p 5432:5432 -d postgres
```

### (Optional) Using the o!TR Demo Database

We have curated a demo database with a few years of tournament data from popular tournaments like OWC. You can choose to use this sample data over starting with an empty database if you wish. You can download the SQL file from [here](). Once downloaded, execute the following commands.

```sh
# Copy the SQL file to the container
docker cp demodb.sql {CONTAINER_NAME_OR_ID}:/demodb.sql

# Execute the SQL file with psql
docker exec -it {CONTAINER_NAME_OR_ID} psql -U {POSTGRES_USER} -d {DATABASE_NAME} -f /demodb.sql
```

### Configuring the API

Now that you have a PostgreSQL setup and dependencies installed, you are ready to configure and build the API.

Clone the API, and create a config file at `otr-api/API/appsettings.json`. Fill in the values from the `example.appsettings.json` template.

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
`"Server={DOMAIN};Port={PORT};User Id={POSTGRES_USER};Password={POSTGRES_PASSWORD};Include Error Detail=true;"`

An example connection string for local development would look like:\
`"Server=localhost;Port=5432;User Id=postgres;Password=otrdev;Include Error Detail=true;"`

#### Osu

Note that currently the config requires both a v1 osu! API key as well as v2 oath credentials, however the use of the v1 API will be phased out at some point. When creating the oath client, set the redirect url to `localhost:8000/auth`

#### Jwt

The `Key` field is the secret the API uses to encode and decode Jason Web Tokens. You can set this to any random string.

<!-- Needs clarification -->
The `Audience` field refers to the frontend webserver. You can set this to `"localhost:3000"`.

#### Auth

Need more information