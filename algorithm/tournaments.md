# Tournament Eligibility / Submission FAQ

Please keep in mind that the o!TR team has final judgment on whether a tournament or match is deemed fair for rating use, but we will work by the following principles and make judgments in good faith.

## Which match links should I include from the tournament?
Do not include qualifiers or tryouts, but do include all matches from group and bracket stages. Make sure the tournament has fully concluded. Do not worry about filtering out for warmups, but please double check that you're not submitting empty match links, showmatches, or asynchronous matches. Removing bad data before submitting helps us significantly.

## What constitutes an acceptable tournament or match?
Tournaments must be at least RO16 single elimination or RO8 double elimination, have concluded all play, and adhere to the [official support documentation](https://osu.ppy.sh/wiki/en/Tournaments/Official_support#tournaments). We do not require all tournaments to be badge-eligible, nor do they need to adhere to all provisions in that wiki. Tournaments must have the following, at a minimum:
* Document all match data to an acceptable standard (preferably on a public Google sheet).
* Not have significant lapses in data, such as full rounds missing. Exceptions are made for very old tournaments for the sake of preservation, but modern tournaments will generally be skipped if any rounds are missing.
* Though not to the same degree as badging standards, be organized to an acceptable standard. For example, tournaments with obvious rigging are not included, even if the matches themselves are fair. So long as things are "generally competitively sound," we will generally favor including it.
* Again not to the same degree as badging standards, target an acceptably competitive range of players. For example, tournaments restricted to ranks 200,000 or worse, or regional tournaments restricted to ranks 100,000 or worse, may not be accepted due to the prevalence of isolated players who do not play in other tournaments.
* Have a forum post or wiki page on the osu! website.

To keep the match cost formula sensible, maps with non-standard win conditions (Tag, Relax, ScoreV1, Accuracy) will not be included in rating calculations, so only submit tournaments with **ScoreV2** as the primary win condition. Tournaments with varying team sizes (e.g. [Tayuno's Standout Cup](https://osu.ppy.sh/community/forums/topics/1492360?n=1)) or battle-royale formats (e.g. [osu! Battle Royale 5](https://osu.ppy.sh/community/forums/topics/1502313?n=1)) should also not be submitted.

Besides this, tournaments which **do not allow players to play at their full competitive strength** throughout the whole match or **stray too far from traditional competitive standards** should not be included. For example, [BATBALL's Gimmick Emporium](https://osu.ppy.sh/community/forums/topics/1767170?n=1) is currently considered barely acceptable, while [Pokemon Battle Tournament](https://osu.ppy.sh/community/forums/topics/1790791?n=1) is considered barely unacceptable. Both have limitations on how much team members can play, but the latter potentially changes team size mid-match. If the pools are unusual (e.g. [Old Map Fantasy World Cup](https://osu.ppy.sh/community/forums/topics/1359817?n=1)), that is okay as long as it does not create a totally different competitive environment (e.g. [Ale's Epic Low SR Tournament](https://osu.ppy.sh/community/forums/topics/1390305?n=1)). 

## Should different tiers or divisions of a tournament go in the same submission?
Carefully check how the forum post defines 'tier'. Tiered tournaments where people of different rank ranges play together, like [Broccoli Cup 3](https://osu.ppy.sh/community/forums/topics/1829892?n=1), should be submitted as a single tournament. When submitting, put the best rank range as the rank restriction (750 for Broccoli Cup 3). On the other hand, forum posts with multiple brackets for different regions or rank ranges, like [Dio's Autumn Singles](https://osu.ppy.sh/community/forums/topics/1086855?n=1) or [5WC Major / Minor League](https://osu.ppy.sh/community/forums/topics/1541806?n=1), should have each bracket submitted as a different tournament. The general rule here is: **one submission per bracket.**

## How far back can tournaments go? Can I submit a tournament from 2015?
Yes, a more complete rating history is always good! However, please make sure to do your own quality checks first. Old tournaments may have incomplete match data and only minimal records of mappools and registered teams.

## The tournament I'd like to submit is missing some matches.
If the tournament has not concluded, do not submit it yet. If the tournament is missing a few matches on the sheet because it's an old tournament that did not have modern data-preservation standards in mind, that's fine - submit without those. If you’re not sure, feel free to ask in the [Discord](https://discord.gg/R53AwX2tJA) or message the tournament organizers to see if they have the missing links.

## Is it okay for different tournaments to have the same abbreviation? What about weird abbreviations?
It is okay for multiple tournaments to share the same abbreviation, since we only ask for the abbreviation to help with verification of MP links. However, remember to check whether different tiers or brackets from the same forum post use different abbreviations (e.g. minor leagues may add an "ML") and submit those brackets separately if so. Some tournaments like IGTS add the name of the round (e.g. "RO16" or "F") to the MP link. In those cases, **only** submit the main abbreviation (e.g. "IGTS" instead of "IGTS RO16") and submit the entire tournament together.

## How do I grab MP links from a sheet quickly without clicking on every single one?
There are two options. The first is to contact the tournament host or spreadsheet owner and ask them for a list. It is usually easier for a staff member to get them. The second is to use Google's  `=IMPORTRANGE()` spreadsheet function on the cells with the match links to import them to a new sheet. You'll then have lots of cells that look like "MP Link", and you can extract the match links with a script detailed in this [Stack Overflow answer](https://stackoverflow.com/a/67206954). When in doubt, have the tournamnt's sheeters contact us or ask in the [Discord](https://discord.gg/R53AwX2tJA).

## I think something is wrong!
There will be a system soon to allow such corrections to be reported. Thanks for noticing!
