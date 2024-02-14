# Tournament Eligibility / Submission FAQ

Please keep in mind that the o!TR team has final judgment on whether a tournament or match is deemed fair for rating use, but we will work by the following principles and make judgments in good faith.

## Which MP links should I include from the tournament?
Do not include qualifiers or tryouts, but include all head-to-head matches from group and bracket stages (in particular, make sure the tournament has already concluded). You don't have to worry about filtering out for warmups, but try to double check that you're not submitting empty MP links or showmatches.

## What constitutes an acceptable tournament or match?
Tournaments must be at least RO16 single elimination, have concluded all play, and abide by the [osu! tournament ideals](https://osu.ppy.sh/wiki/en/Tournaments/Official_support#tournaments). To keep the match cost formula sensible, maps with non-standard win conditions (tag, relax, ScoreV1, accuracy) will not be included in rating calculations, so only submit tournaments with **ScoreV2** as the primary win condition. Tournaments with varying team sizes (e.g. [Tayuno's Standout Cup](https://osu.ppy.sh/community/forums/topics/1492360?n=1)) or battle-royale formats (e.g. [osu! Battle Royale 5](https://osu.ppy.sh/community/forums/topics/1502313?n=1)) should also not be submitted.

Besides this, tournaments which **do not allow players to play at their full competitive strength** throughout the whole match or **stray too far from the traditional head-to-head format** should not be included. For example, [BATBALL's Gimmick Emporium](https://osu.ppy.sh/community/forums/topics/1767170?n=1) is currently considered barely acceptable, while [Pokemon Battle Tournament](https://osu.ppy.sh/community/forums/topics/1790791?n=1) is considered barely unacceptable (both have limitations on how much team members can play, but the latter potentially changes team size mid-match). If the pools are unusual (e.g. [Old Map Fantasy World Cup](https://osu.ppy.sh/community/forums/topics/1359817?n=1)), that is okay as long as it does not create a totally different competitive environment (e.g. [Ale's Epic Low SR Tournament](https://osu.ppy.sh/community/forums/topics/1390305?n=1)). 

## Should different tiers or divisions of a tournament go in the same submission?
Check carefully what a forum post means by the word "tier." Tiered tournaments where people of different rank ranges play together, like Broccoli Cup, should be submitted as a single tournament (put the best rank range as the rank restriction). On the other hand, forum posts with multiple brackets for different regions or rank ranges, like Dio's Autumn Singles or 5WC minor league, should have each bracket submitted as a different tournament. The rule here is: one submission per bracket.

## How far back can tournaments go? Can I submit a tournament from 2015?
Yes, more complete rating history is always good! However, please make sure to do your own quality checks first - old tournaments often have incomplete match data or use rulesets that are now considered non-standard.

## The tournament I'd like to submit is missing some matches.
If the tournament has not concluded, do not submit it yet. If the tournament is just missing a few matches on the sheet because it's an old sheet which was not properly updated, that's fine - submit without those. If you’re not sure, feel free to ask in the [Discord](https://discord.gg/R53AwX2tJA) or message the tournament organizers to see if they have the missing links.

## Is it okay for different tournaments to have the same abbreviation? / Something weird is going on with this tournament's abbreviation.
Same abbreviations are fine - we ask for the abbreviation to help with verification of MP links. However, remember to check whether different tiers or brackets from the same forum post use different abbreviations (e.g. minor leagues may add an "ML")and submit those brackets separately if so. Some tournaments like IGTS add the name of the round ("RO16" or "F") to the MP link; in those cases **only** submit the initial abbreviation ("IGTS" instead of "IGTS RO16") and submit the entire tournament together.

## How do I grab MP links from a sheet quickly without clicking on every single one?
There are two options. The first is to contact the sheeter and ask them for a list (since it's usually easier for a staff member to get them from the ref sheet). The second is to **importrange** the cells with the MP links into a separate spreadsheet. You'll then have a bunch of cells that look like "MP Link", and you can extract the match links with a script detailed in this [Stack Overflow answer](https://stackoverflow.com/a/67206954). When in doubt, have the tournamnt's sheeters contact us or ask in the Discord.

## An MP link is missing or should not be included in an accepted tournament. / My match cost is incorrect because of warmups or for-fun maps. / I think an accepted tournament should not be included under the current guidelines.
There will be a ticket system soon to allow such corrections to be made. Thanks for noticing!
