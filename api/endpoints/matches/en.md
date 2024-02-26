# Matches

### Submit Matches for Verification
( **PUBLIC** )\
Submit a tournament and associated matches to be verified for rating calculation

Request\
( **POST** ) `/matches/batch`

Query Parameters\
`verified` boolean *optional*\
Setting this to true will verify that the `submitterid` is an ( **ADMIN** ) user. Will result in a 401 if not

Body Parameters\
See [TournamentWebSubmission](/api/objects/en.md#tournamentwebsubmission)

Response Format\
HTTP Response ( 200 | 400 | 401 )

Example Request
```js
const requestBody = JSON.stringify({
  "name": "5 Digit World Cup",
  "abbreviation": "5WC",
  "forumpost": "https://osu.ppy.sh/community/forums/topics/1874523",
  "rankrangelowerbound": 10000,
  "mode": 0,
  "teamsize": 8,
  "submitterid": 18068913,
  "ids": [18068913, 18068914, 18068915, ...],
});

fetch("https://api.otr.stagec.xyz/matches/batch", {
  method: "POST",
  body: requestBody,
});
```

---

### Refresh Automation Checks

( **ADMIN** )\
Marks all matches as needing automation checks

Request\
( **POST** ) `/matches/refresh/automations`

Response Format\
Http Response ( 200 | 401 )

---

### Get All Verified Match Ids

( **ADMIN** )\
Returns a list of all verified match ids

Request\
( **GET** ) `/matches/ids`

Response Format
| Field | Type |
| ----- | ---- |
| { ? } | integer[] |

---

### Get Match By Id

( **ADMIN** )\
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

( **ADMIN** )\
Converts a list of match ids to Match objects

Request\
( **POST** ) `/matches/convert`

Body Parameters\
`ids` integer[]

Response Format\
Returns [Match](/api/objects/en.md#match)[]

---

### Get All Duplicate Groups

( **ADMIN** )\
Retrieves all known duplicate match groups

Request\
( **GET** ) `/matches/duplicates`

Response Format\
Returns [MatchDuplicateCollection](/api/objects/en.md#matchduplicatecollection)[]

---

### Mark a Match as Duplicate

( **ADMIN** )\
Mark a match as a confirmed or denied duplicate of the root

Request\
( **POST** ) `/matches/duplicate`

Query Parameters\
`rootid` string\
The root match id

`confirmedduplicate` boolean\
Whether the match is confirmed or denied as a duplicate

Response Format\
Http Response ( 200 | 400 | 401 )

---

### Get All Matches for Player

( **ADMIN** )\
Get all matches the player was a part of

Request\
( **GET** ) `/matches/player/{osuid}`

URL Parameters\
`osuid` integer\
The osu! id of the target player

Response Format\
Returns [Match](/api/objects/en.md#match)[]

---

### Get osu! Match Id From otr Match Id

( **ADMIN** )
Get the osu! match id searching by otr match id

Request\
( **GET** ) `/matches/{id}/osuid`

URL Parameters\
`id` integer\
The target otr match id

Response Format
| Field | Type |
| ----- | ---- |
| { ? } | integer |

---

### Get Match Id Mapping

( **PUBLIC** ) ??\
Get the unique mapping of otr match id to osu! match id

Request\
( **GET** ) `/matches/id-mapping`

Response Format\
Returns [MatchIdMapping](/api/objects/en.md#matchidmapping)

---