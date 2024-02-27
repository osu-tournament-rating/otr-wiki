# Players

### Get All Players

Get all players

Request\
( **GET** ) `/players/all`

Response Format\
Returns [Player](/api/objects/en.md#player)[]

---

### Get Player Info From User Id

Get player info searching by userId

Request\
( **GET** ) `/players/{userId}/info`

URL Parameters\
`userId` integer\
The id of the target player

Response Format\
Returns [PlayerInfo](/api/objects/en.md#playerinfo)

---

### Get Player Info From Username

Get player info searching by userId

Request\
( **GET** ) `/players/{username}/info`

URL Parameters\
`username` integer\
The osu! username of the target player

Response Format\
Returns [PlayerInfo](/api/objects/en.md#playerinfo)

---

### Get Id of Player From osu! Id

Get player id searching by osu! id

Request\
( **GET** ) `/players/{osuId}/id`

URL Parameters\
`osuId` integer\
The osu! id of the target player

Response Format
| Field | Type |
| ----- | ---- |
| { ? } | integer |

---

### Get osu! Id of Player From Id

Get player osu! id searching by id

Request\
( **GET** ) `/players/{id}/osuid`

URL Parameters\
`id` integer\
The id of the target player

Response Format
| Field | Type |
| ----- | ---- |
| { ? } | integer |

---

### Get All Player Rank Info

Get all player rank info

Request\
( **GET** ) `/players/ranks/all`

Response Format\
Returns [PlayerRanks](/api/objects/en.md#playerranks)[]

---

### Get Leaderboard Info

Get top 50 player ratings by mode

Request\
( **GET** ) `/players/leaderboard/{mode}`

URL Parameters\
`mode` integer\
Desired gamemode

Query Parameters\
`gamemode` integer\
Desired gamemode

Response Format\
Returns [PlayerRating](/api/objects/en.md#playerrating)[]

---

### Get All Player Id Mappings

Get the unique mappings of o!TR player id to osu! player id

Request\
( **GET** ) `/players/id-mapping`

Response Format\
Returns [PlayerIdMapping](/api/objects/en.md#playeridmapping)[]

---

### Get All Player Country Mappings

Get the mappings of o!TR player id to osu! country code

Request\
( **GET** ) `/players/ranks/all`

Response Format\
Returns [PlayerCountryMapping](/api/objects/en.md#playercountrymapping)[]

---