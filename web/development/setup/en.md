# o!TR Web Setup

## Prerequisites

o!TR Web depends on the API for all web requests. By extension, the database will need to be configured as well. Ensure these processes are running in the background before running o!TR Web.

- [o!TR API Setup](/api/development/setup/en.md)
- [o!TR Database Setup](/api/maintenance/database/en.md)
- [Node.js](https://nodejs.org/en) (v21 or later)

## Environment Configuration

- Rename the `.env.example` file to `.env`.
- Set the `REACT_APP_OSU_CLIENT_ID` to your osu! API v2 client id. Ensure one of the callback URLs is set to `http://localhost:3000/auth` in your osu! client's configuration settings. You can configure a new client under the 'OAuth' section in your [osu! settings page](https://osu.ppy.sh/home/account/edit).

## Install

Install the necessary dependencies:

```
npm i
```

## Run

Run the application:

```
npm run dev
```