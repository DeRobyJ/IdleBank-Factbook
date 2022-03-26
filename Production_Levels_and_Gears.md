## Production, Levels and Gears

The incremental part of the game is to use money you produce naturally to upgrade the production rate itself.


### Production rate

The production is expressed as the quantity of money produced every hour.
It's calculated on the following formula, but for level 0, which has no production.

```
L: current level
G: multiplier based on current gears

Natural Hourly Production Rate = 90 + L*10 + Floor(L / 16) * (L - 15)
Geared Up Hourly Production Rate = Floor ( G * Natural Hourly Production Rate )

```

Some examples

Level | Natural HPR
--- | ---
0 | 0
1 | 100
2 | 110
3 | 120
14 | 230
15 | 240
16 | 251
17 | 262
18 | 273
30 | 405
31 | 416
32 | 444
33 | 456
34 | 468
50 | 695
100 | 1600
200 | 4310
300 | 8220
400 | 13715
500 | 20125
750 | 41400
1000 | 71160
10000 | 6340715


### Production upgrade costs

Every player starts a level 0, with no hourly production.
The cost for the first lever is 1 block of the player's faction and 15 money of the player's currency.

```
P: Natural Hourly Production Rate of current level
L: next level
Multiplier = ((SquareRoot(L + 100) - 10) / 2)
Money Cost = Floor( P * Multiplier )

if L divisible by 10 (like 10, 20, 30, 50, 100, 150, ..)
    Block Cost = Floor( L / 10 )
if L divisible by 3 and not by 10 (3, 6, 9, 15, 27, 33, ..)
    Block Cost = Floor( L / 30 )
if L even but not divisible by 3 or 10 (2, 4, 8, 14, 16, 22, ..)
    Block Cost = Floor( L / 50 )
if L odd and not divisible by 3 or 10 (1, 5, 7, 11, 13, 17, ..)
    Block Cost = Floor( L / 100 )

However, the Block Cost can't be more than 5
```

Level | Multiplier | Block Cost
--- | --- | ---
0 | 0 | 1
1 | 0.025 | 0
2 | 0.05 | 0
3 | 0.074 | 0
4 | 0.099 | 0
5 | 0.123 | 0
10 | 0.244 | 1
15 | 0.362 | 0
20 | 0.477 | 2
30 | 0.7 | 3
40 | 0.916 | 4
50 | 1.124 | 5
100 | 2.071 | 5
200 | 3.66 | 5
300 | 5 | 5
500 | 7.247 | 5
1000 | 11.583 | 5
10000 | 45.249 | 5


### Gears

Gearing up is paying a certain amount of levels to get a new gear badge, which in turns rewards the player with increased money production rates.

```
if player currently has no gears
  Level Cost = 50
else
  Level Cost = 100 * Current Number of Gears


Production Multiplier = Multiplication, for every faction, of ( 1 + 0.1 * Number of gears from that faction )

```

FED gears | ECB gears | PBC gears | total gears | Production Multiplier
--- | --- | --- | --- | ---
0 | 0 | 0 | 0 | 1
1 | 0 | 0 | 1 | 1.1
2 | 0 | 0 | 2 | 1.2
