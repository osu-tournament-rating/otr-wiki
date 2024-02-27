# Object Structures

### AggregatePlayerMatchStats

Represents an aggregate of match statistics for a player during a given period of time

| Field     | Type     | Description |
| :-------- | :------- | :---------- |
| averageMatchCostAggregate | float | Average match cost during the given period
| highestRating | float |
| highestGlobalRank | integer |
| highestCountryRank | integer |
| highestPercentile | float | Peak rating percentile achieved during the given period |
| ratingGained | float | The amount of rating gained during the given period |
| gamesWon | integer |
| gamesLost | integer |
| gamesPlayed | integer |
| matchesWon | integer |
| matchesLost | integer |
| matchesPlayed | integer |
| gameWinrate | float | A value between 0 and 1 representing game win rate percentage |
| matchWinrate | float | A value between 0 and 1 representing match win rate percentage |
| bestWinstreak | integer | Most amount of matches won in a row during the given period |
| matchAverageScoreAggregate | float | The average score across the entire lobby in every match the player has played in during the given period. Includes scores for games the player may not have been in for |
| matchAverageMissesAggregate | float | The average miss count across the lobby for every game in every match the player played in during the given period |
| matchAverageAccuracyAggregate | float | The average accuracy across the lobby for every game in every match the player played in during the given period |
| averageGamesPlayedAggregate | float | The average amount of games played per match during the given period |
| periodStart | timestamp | The beginning of the period for which statistics were calculated |
| periodEnd | timestamp | The end of the period for which statistics were calculated |

Optional fields:

| Field     | Type     | Description |
| :-------- | :------- | :---------- |
| averageTeammateRating | float | The average rating of the player's teammates during the period. This average does not include the player's own rating |
| averageOpponentRating | float | The average rating of the player's opponents during the period |
| mostPlayedTeammateName | string | The name of the teammate played with the most during the given period |
| mostPlayedOpponentName | string | The name of the opponent played against the most during the given period |
| bestTeammateName | string | The name of the teammate who held the highest rating during the given period. If the period is looking to the present, this will be the teammate with the highest current rating |

---

### BaseStats

Represents general stats that are current and not time specific

| Field     | Type     | Description |
| :-------- | :------- | :---------- |
| playerId | integer |
| rating | float |
| volatility | float | { Blank Description } |
| mode | integer |
| percentile | float |
| matchesPlayed | integer |
| winrate | float |
| highestGlobalRank | integer |
| globalRank | integer |
| countryRank | integer |
| averageMatchCost | float |
| tournamentsPlayed | integer |
| rankProgress | [RankProgress](#rankprogress) |
| isProvisional | boolean | { Blank Description } |

---

### Beatmap

Represents a beatmap

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| artist | string |
| beatmapId | integer |
| bpm | float |
| mapperId | integer |
| mapperName | string |
| sr | float |
| aimDiff | float |
| speedDiff | float |
| cs | float |
| ar | float |
| hp | float |
| od | float |
| drainTime | float |
| length | float |
| title | string |
| diffName | string |
| gameMode | integer |
| circleCount | integer |
| sliderCount | integer |
| spinnerCount | integer |
| maxCombo | integer |
| created | timestamp |
| games | [Game](#game)[] |

---

### Game

Represents a single game played within a match

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| playMode | integer |
| scoringType | integer |
| teamType | integer |
| mods | integer |
| gameId | integer |
| startTime | timestamp |
| matchScores | [MatchScore](#matchscore)[] |

Optional fields:
| Field     | Type     | Description |
| :-------- | :------- | :---------- |
| endTime | timestamp |
| beatmap | Beatmap |

---

### Match

Represents an entire tournament match

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| matchId | integer |
| mode | integer |
| games | [Game](#game)[] |

Optional fields:
| Field     | Type     |
| :-------- | :------- |
| startTime | timestamp |
| endTime | timestamp |
| verificationStatus | integer |

---

### MatchDuplicate

Represents a match suspected of or confirmed to be a duplicate

| Field     | Type     |
| :-------- | :------- |
| osuMatchId | integer |
| name | string |

Optional fields:
| Field     | Type     |
| :-------- | :------- |
| verifiedAsDuplicate | boolean |
| verifiedByUsername | string |
| verifiedByUserId | integer |

---

### MatchDuplicateCollection

Represents a collection of matches suspected of or confirmed to be duplicates of one another

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| name | string |
| osuMatchId | integer |
| suspectedDuplicates | [MatchDuplicate](#matchduplicate)[]

---

### MatchIdMapping

Represents a mapping of the otr match id to it's respective osu! match id

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| osuMatchId | integer |

---

### Player

Represents a player

| Field     | Type     |
| :-------- | :------- |
| username | string |
| country | string |

---

### PlayerCountryMapping

Represents the unique mapping of o!TR player id to osu! country code

| Field     | Type     |
| :-------- | :------- |
| playerId | integer |
| country | string |

---

### PlayerIdMapping

Represents the unique mapping of o!TR player id to osu! player id

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| osuId | integer |

---

### PlayerInfo

Represents a player with additional info

| Field     | Type     |
| :-------- | :------- |
| id  | integer |
| osuId | integer |
| username | string |
| country | string |

---

### PlayerRanks

Represents osu! rankings for a player

| Field     | Type     |
| :-------- | :------- |
| id | integer |
| osuId | integer |

Optional fields:

| Field     | Type     |
| :-------- | :------- |
| rankStandard | integer |
| rankTaiko | integer |
| rankCatch | integer |
| rankMania | integer |
| earliestOsuGlobalRank | integer |
| earliestOsuGlobalRankDate | timestamp |
| earliestTaikoGlobalRank | integer |
| earliestTaikoGlobalRankDate | timestamp |
| earliestCatchGlobalRank | integer |
| earliestCatchGlobalRankDate | timestamp |
| earliestManiaGlobalRank | integer |
| earliestManiaGlobalRankDate | timestamp |

---

### PlayerStats

{ Blank Description }

| Field     | Type     |
| :-------- | :------- |
| playerInfo | [PlayerInfo](#PlayerInfo) |
| baseStats | [BaseStats](#BaseStats) |
| matchStats | [AggregatePlayerMatchStats](#AggregatePlayerMatchStats) |
| modStats | [PlayerModStats](#PlayerModStats) |
| frequentTeammates | [PlayerFrequency](#PlayerFrequency) |
| frequentOpponents | [PlayerFrequency](#PlayerFrequency) |
| ratingStats | [MatchRatingStats](#MatchRatingStats) |

---

### Tournament

Represents a tournament with basic format information

| Field     | Type     |
| :-------- | :------- |
| name | string |
| abbreviation | string |
| forumUrl | string |
| rankRangeLowerBound | integer |
| mode | integer |
| teamSize | integer |

### TournamentWebSubmission

Represents a tournament submission

| Field     | Type     | Description |
| :-------- | :------- | --- |
| name  | string |
| abbreviation | string |
| forumPost | string |
| rankRangeLowerBound | integer |
| mode | integer |
| teamSize | integer |
| submitterId | integer |
| ids | integer[] | List of tournament match ids |

