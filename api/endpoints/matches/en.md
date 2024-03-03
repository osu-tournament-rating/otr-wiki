# Matches

### Submit Matches for Verification

( **user** ) ( **submit** )\
Submit a tournament and associated matches to be verified for rating calculation

Request\
( **POST** ) `/matches/batch`

Query Parameters\
`verified` boolean *optional*\
Setting `verified` to `true` will assert that the `submitterId` has the ( **verifier** ) scope

Body Parameters\
See [TournamentWebSubmission](/api/objects/en.md#tournamentwebsubmission)

Example Request
```js
const requestBody = JSON.stringify({
  "name": "5 Digit World Cup",
  "abbreviation": "5WC",
  "forumPost": "https://osu.ppy.sh/community/forums/topics/1874523",
  "rankRangeLowerBound": 10000,
  "mode": 0,
  "teamSize": 4,
  "submitterId": 18068913,
  "ids": [18068913, 18068914, 18068915, ...],
});

fetch("https://api.otr.stagec.xyz/matches/batch", {
  method: "POST",
  body: requestBody,
});
```

---

### Refresh Automation Checks

Marks all matches as needing automation checks

Request\
( **POST** ) `/matches/refresh/automations`

---

### Get All Verified Match Ids

Returns a list of all verified match ids

Request\
( **GET** ) `/matches/ids`

Response Format\
Returns integer[]

---

### Get Match by Id

Returns a match object by its id

Request\
( **GET** ) `/matches/{id}`

URL Parameters\
`id` integer\
The match id of the target match

Response Format\
Returns [Match](/api/objects/en.md#match)

---

### Convert a List of Match Ids to Match Objects

( **user** )\
Converts a list of match ids to Match objects

Request\
( **POST** ) `/matches/convert`

Body Parameters\
`ids` integer[]

Response Format\
Returns [Match](/api/objects/en.md#match)[]

---

### Get All Duplicate Groups

Retrieves all known duplicate match groups

Request\
( **GET** ) `/matches/duplicates`

Response Format\
Returns [MatchDuplicateCollection](/api/objects/en.md#matchduplicatecollection)[]

---

### Mark a Match as Duplicate

Mark a match as a confirmed or denied duplicate of the root

Request\
( **POST** ) `/matches/duplicate`

Query Parameters\
`rootId` string\
The root match id

`confirmedDuplicate` boolean\
Whether the match is confirmed or denied as a duplicate

---

### Get All Matches for Player

Get all matches the player was a part of

Request\
( **GET** ) `/matches/player/{osuId}`

URL Parameters\
`osuId` integer\
The osu! id of the target player

Response Format\
Returns [Match](/api/objects/en.md#match)[]

---

### Get osu! Match Id From o!TR Match Id

Get the osu! match id searching by o!TR match id

Request\
( **GET** ) `/matches/{id}/osuid`

URL Parameters\
`id` integer\
The target o!TR match id

Response Format\
Returns integer

---

### Get All Match Id Mappings

( **user** )\
Get all unique mappings of o!TR match id to osu! match id

Request\
( **GET** ) `/matches/id-mapping`

Response Format\
Returns [MatchIdMapping](/api/objects/en.md#matchidmapping)[]

---