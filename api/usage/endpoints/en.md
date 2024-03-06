# Endpoints

## Base URL

The base URL is: `https://api.otr.stagec.xyz/`

## List of Documented Routes

- [/beatmaps](./beatmaps/en.md)
- [/matches](./matches/en.md)
- [/players](./players/en.md)

## Accept Header

The API supports the following content types for use in the `Accept` header.

- `text/plain`
- `application/json`
- `text/json`

## Format

Using the entry for [`/matches/batch`](./matches/en.md#submit-matches-for-verification) as an example, this is a breakdown of the formatting for endpoint documentation.

### Header

The header for each section is a very brief description of the outcome when interacting with the endpoint.

```md
### Submit Matches for Verification
```

### Scopes

The first element below the header will be a list of [scopes](/api/scopes/en.md) required for accessing the endpoint if applicable. These will list the *minimum* level of permission required, as well as any special scopes such as ( **submit** ) or ( **verifier** ).

Keep in mind certain scopes such as ( **admin** ) and ( **system** ) are *implied* with full access to the API. If there are no scopes listed for an entry, that endpoint is likely private and has no way of being accessed by typical users.

```md
( **user** ) ( **submit** )
```

### Description

Below the scopes will be a more detailed description of the function of the endpoint.

```md
Submit a tournament and associated matches to be verified for rating calculation
```

### Request Type

Below the description will be the request type. HTTP method followed by path.

```md
Request
( **POST** ) `/matches/batch`
```

### Parameters

Below the request type will be a list of any applicable parameters. Parameters will always be listed in the order of URL parameters, query parameters, and lastly body parameters.

Each parameter is formatted `<name> <type> <optional?>` followed by a description.

```md
Query Parameters
`verified` boolean *optional*
Setting `verified` to `true` will assert that the `submitterId` has the ( **verifier** ) scope

Body Parameters
See [TournamentWebSubmission](/api/objects/en.md#tournamentwebsubmission)
```

### Example Request

Finally, each entry will contain an example request written in Javascript.

```js
Example Request

const requestBody = JSON.stringify({
  "name": "5 Digit World Cup",
  "abbreviation": "5WC",
  "forumPost": "https://osu.ppy.sh/community/forums/topics/1874523",
  "rankRangeLowerBound": 10000,
  "mode": 0,
  "teamSize": 8,
  "submitterId": 18068913,
  "ids": [18068913, 18068914, 18068915, ...],
});

fetch("https://api.otr.stagec.xyz/matches/batch", {
  method: "POST",
  body: requestBody,
});
```