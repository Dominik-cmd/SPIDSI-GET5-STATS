# SPIDSI-GET5-STATS (EC18)


## Competing teams - 19 teams
```
SELECT name FROM get5.team WHERE get5.team.id > 2; -- First 2 were test teams
```

- Bejz dol s kocije
- insomnius bastards
- 21arches
- Team UVI
- HareKrištan
- Speed Logic Gaming
- KILLSHOT
- tihbot
- Agregat 10
- Peanuts
- cebabula
- BALLERJI
- Huns
- simdi hadzir
- premisli2x
- [SpricerSquad]
- OMG Clan
- Team-Phase
- HypedRetards

## All matches + winners - 52 matches
```
SELECT t.name AS Team1, t1.name AS Team2, t2.name AS Winner
FROM get5.match m 
INNER JOIN get5.team t 
	ON m.team1_id = t.id 
INNER JOIN get5.team t1 
	ON m.team2_id = t1.id
INNER JOIN get5.team t2 
	ON m.winner = t2.id
WHERE t.id > 2 AND t1.id > 2 
AND m.end_time IS NOT NULL
ORDER BY m.start_time DESC
```


- Team1, Team2, Winner
- Agregat 10	HareKrištan	Agregat 10
- BALLERJI	Team UVI	Team UVI
- HareKrištan	BALLERJI	HareKrištan
- Agregat 10	Team UVI	Agregat 10
- tihbot	HareKrištan	HareKrištan
- 21arches	Team UVI	Team UVI
- BALLERJI	premisli2x	BALLERJI
- [SpricerSquad]	HypedRetards	[SpricerSquad]
- Agregat 10	cebabula	Agregat 10
- 21arches	insomnius bastards	21arches
- cebabula	Peanuts	cebabula
- Team UVI	Speed Logic Gaming	Team UVI
- insomnius bastards	Peanuts	Peanuts
- Agregat 10	simdi hadzir	Agregat 10
- BALLERJI	Huns	BALLERJI
- simdi hadzir	cebabula	cebabula
- Peanuts	HypedRetards	Peanuts
- HareKrištan	KILLSHOT	HareKrištan
- 21arches	Speed Logic Gaming	21arches
- [SpricerSquad]	Huns	Huns
- tihbot	Bejz dol s kocije	tihbot
- simdi hadzir	OMG Clan	simdi hadzir
- Team-Phase	premisli2x	premisli2x
- Team UVI	Agregat 10	Agregat 10
- Agregat 10	insomnius bastards	Agregat 10
- 21arches	cebabula	21arches
- Team-Phase	KILLSHOT	Team-Phase
- tihbot	[SpricerSquad]	tihbot
- OMG Clan	Speed Logic Gaming	Speed Logic Gaming
- Team UVI	insomnius bastards	Team UVI
- 21arches	simdi hadzir	21arches
- tihbot	KILLSHOT	tihbot
- BALLERJI	Bejz dol s kocije	BALLERJI
- Huns	Team-Phase	Team-Phase
- cebabula	Speed Logic Gaming	cebabula
- HareKrištan	premisli2x	HareKrištan
- Peanuts	Agregat 10	Agregat 10
- insomnius bastards	HypedRetards	insomnius bastards
- tihbot	Huns	tihbot
- premisli2x	BALLERJI	BALLERJI
- HareKrištan	Bejz dol s kocije	HareKrištan
- Team UVI	Peanuts	Team UVI
- [SpricerSquad]	KILLSHOT	KILLSHOT
- OMG Clan	21arches	21arches
- BALLERJI	HareKrištan	BALLERJI
- tihbot	Team-Phase	tihbot
- Speed Logic Gaming	simdi hadzir	Speed Logic Gaming
- Team UVI	HypedRetards	Team UVI
- Bejz dol s kocije	premisli2x	premisli2x
- [SpricerSquad]	Team-Phase	Team-Phase
- cebabula	OMG Clan	cebabula
- Agregat 10	HypedRetards	Agregat 10

## Longest match - Agregat 10 vs HareKrištan (finals) 157 minuts and 31 seconds

```
SELECT t.name AS Team1, t1.name AS Team2, t2.name AS Winner, m.start_time AS Start_Time, m.end_time AS End_Time,
UNIX_TIMESTAMP(m.end_time) - UNIX_TIMESTAMP(m.start_time) AS GAP 
FROM get5.match m 
INNER JOIN get5.team t 
	ON m.team1_id = t.id 
INNER JOIN get5.team t1 
	ON m.team2_id = t1.id
INNER JOIN get5.team t2 
	ON m.winner = t2.id
WHERE t.id > 2 AND t1.id > 2 
AND m.end_time IS NOT NULL
ORDER BY m.start_time DESC
```

## Map stats
```
SELECT count(map_name), map_name FROM get5.map_stats
group by map_name
order by count(map_name) DESC
```

- 23	de_mirage
- 20	de_cache
- 8	de_inferno
- 6	de_train
- 4	de_overpass
- 2	de_nuke
- 1	de_dust2

Total rounds played across all maps: 1485



## Player stats

#### 246	 - ElouS -- kills
#### 198	 - FOOLZZ -- deaths
#### 56	 - Grmekk $ -- assists
#### 19	 - ZELElegend cs.money -- flashbang_assists
#### 3	 - reyn -- teamkills
#### 3	 - Murka gamdom.com -- suicides
#### 147	 - ElouS -- headshot_kills
#### 27128	 - ElouS -- damage
#### 32	 - PORKA -- bomb_plants
#### 7	 - r0ck -- bomb defuses

```
SELECT HSKILLS/kills, steamId
FROM (SELECT sum(kills)AS KILLS, sum(deaths) AS DEATHS, sum(headshot_kills) AS HSKILLS, steam_id AS steamId FROM get5.player_stats GROUP BY steam_id) D
ORDER BY HSKILLS/kills DESC
```

#### TOP RATINGS:

###### Rating (K/R)
- 1.6806	- saveeey
- 1.5181	- Chill
- 1.4636	- r0ck
- 1.4583	- Woozy
- 1.3977	- ElouS

###### HS %
- 64%  - Cuftek// ec18
- 62%  - zagrab
- 61%  - HorrorByMe
- 59%  - ElouS
- 57%  - Nino
