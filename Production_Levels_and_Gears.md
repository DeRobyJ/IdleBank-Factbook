## Production, Levels and Gears

The incremental part of the game is to use money you produce naturally to upgrade the production rate itself.


### Production rate

The production is expressed as the quantity of money produced every hour.
It's calculated on the following formula, but for level 0, which has no production.

```
L: current level
G: current number of gears

Natural Hourly Production Rate = L * 720
Geared Up Hourly Production Rate = Floor ( L * 720 * (1 + G / 10))

```

Some examples

Level | Gears | Hourly Production Rate
--- | --- | ---
10 | 0 | 7200
20 | 0 | 14400
50 | 0 | 36000
10 | 3 | 9360
20 | 3 | 18720
50 | 3 | 46800
10 | 10 | 14400
20 | 10 | 28800
50 | 10 | 72000



### Production upgrade costs

The game progression is defined by the upgrading costs.
To upgrade, the player needs a specific amount of money, which is generated automatically, and a specific amount of blocks, which should be acquired through the other functions of the game.

Both costs have simple formulas

```
L: current level
N: next level (current level + 1)

Money cost: 3 * L^2
Block cost: Floor (N / 10) + 1


Considering
HPR: Hourly Production Rate (without gears) = L * 720

Then
Money cost = HPR * L / 240

Considering
HPR / 240 = Money produced in 15 seconds

Money cost = 15 * L seconds worth of production (without gears)

Considering
G: current number of gears
GHPR: Geared Up Hourly Production Rate = Floor ( HPR * (1 + G / 10))

Then
Money cost = 15 * L / (1 + G / 10) seconds worth of production
```

In the following table, some examples, where T is the time needed to produce the money cost

Level | Gear | T | Block Cost
--- | --- | --- | ---
5 | 0 | 1m15s | 1
10 | 0 | 2m30s | 2
20 | 0 | 5m | 3
50 | 0 | 12m30s | 6
100 | 0 | 25m | 11
5 | 3 | 58s | 1
10 | 3 | 1m55s| 2
20 | 3 | 3m51s | 3
50 | 3 | 9m37s | 6
100 | 3 | 19m14s | 11
5 | 10 | 38s | 1
10 | 10 | 1m15s | 2
20 | 10 | 2m30s | 3
50 | 10 | 6m15s | 6
100 | 10 | 12m30s | 11



### Gears

Gearing up is paying a certain amount of levels to get a new gear badge, which in turns rewards the player with increased money production rates, as seen above.

```
Current number of gears: G


Levels used for the next gear = (G + 1) * 50
Blocks given as prize for gearing up = (G + 1) * 10
```

When gearing up, the player receives a badge of the current faction.
Badges are displayed on the player's Profile Page.
For every badge of a specific faction, the player is given 10 blocks of that faction every 24 hours.
This means that even if the player changes faction, they will keep receiving this small bonus of blocks of past factions.


The badges are also shown on the player's nickname. However, they are summarized if there are too many.
These are the possible symbols:

Symbol | Number of gears
--- | ---
1️⃣ | 5
2️⃣ | 10
3️⃣ | 15
4️⃣ | 20
5️⃣ | 25
6️⃣ | 30
7️⃣ | 35
8️⃣ | 40
9️⃣ | 45
🔟 | 50

Two of these synbols can be displayed together, to summarize a number of gears equal to their sum.
Only the last 1, 2, 3, 4 or 5 gears are shown on the player's nickname.

Additionally, every 100 gears, rather than displaying 🔟🔟, a new set of symbols is used.
They are called "supergears", and they do not currently have important effects for the gameplay.
The symbols follow:

Symbol | Number of gears
--- | ---
💍 | 100
👑 | 200
🗿 | 300
🗽 | 300
🗼 | 300
🚀 | 300
🌋 | 300
🏛 | 300

They work a little differently:
- At gear 100, the 💍 is shown. From 101 to 199, the 💍 is followed by the normal badges and numeric symbols.
- At gear 200, the 👑 is shown instead of the 💍, until gear 299.
- At gear 300, one of the six monument is shown instead of the 👑.
- At gear 400, the 💍 will follow the monument. And at gear 500, the 👑 will take its place.
- Only at gear 600 a second monument is shown. Both monuments will be displayed.

This system goes on until all 6 monuments are shown, followed by the 👑, a 🔟 a 9️⃣ and 4 badges, at gear 2099.

After this, the line of symbols is again reset, this time showing a new preceding symbol:


Symbol | Number of gears
--- | ---
💧 | 2100
🍀 | 4200
🔥 | 6300
⚡️ | 8400

Only one of these elemental symbols is shown, depending on the number of gears.
This system reaches gear 10499 with a badge line that looks like this:
⚡️🗼🚀🌋🏛🗿🗽👑🔟9️⃣💴🌊🪔💶

After that, the current final symbol is displayed and the cycle is repeated.

Symbol | Number of gears
--- | ---
🌟 | 10500

This symbol can appear multiple times, one for every 10500 gears.
