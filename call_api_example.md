```python
from riotwatcher import RiotWatcher, ApiError
```


```python
api_key = ''
my_region = 'KR'
sum_name = '줌짱줌짱'
```


```python
watcher = RiotWatcher(api_key)
```


```python
me = watcher.summoner.by_name(my_region, '줌짱줌짱')
```


```python
me.keys()
```




    dict_keys(['id', 'accountId', 'puuid', 'name', 'profileIconId', 'revisionDate', 'summonerLevel'])




```python
#get match list as a dict
matches = watcher.match.matchlist_by_account(my_region, me['accountId'])
```


```python
matches.keys()
```




    dict_keys(['matches', 'startIndex', 'endIndex', 'totalGames'])




```python
#그동안 해왔던 모든 게임 정보가 저장되어 있는지 확인
print(len(matches['matches']),matches['totalGames'])
```

    100 168



```python
#데이터를 보고 싶은 경기를 선택
match = matches['matches'][0]
```


```python
match
```




    {'platformId': 'KR',
     'gameId': 4071113675,
     'champion': 516,
     'queue': 430,
     'season': 13,
     'timestamp': 1578407735500,
     'role': 'SOLO',
     'lane': 'TOP'}




```python
match_res = watcher.match.by_id(my_region,match['gameId'])
match_data = watcher.match.timeline_by_match(my_region,match['gameId'])
```


```python
match_res.keys()
```




    dict_keys(['gameId', 'platformId', 'gameCreation', 'gameDuration', 'queueId', 'mapId', 'seasonId', 'gameVersion', 'gameMode', 'gameType', 'teams', 'participants', 'participantIdentities'])




```python
match_data.keys()
```




    dict_keys(['frames', 'frameInterval'])




```python
match_data['frames'][1].keys()
```




    dict_keys(['participantFrames', 'events', 'timestamp'])




```python
match_data['frames'][1]['participantFrames']
```




    {'1': {'participantId': 1,
      'position': {'x': 8079, 'y': 3501},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '2': {'participantId': 2,
      'position': {'x': 7313, 'y': 3610},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '3': {'participantId': 3,
      'position': {'x': 3383, 'y': 7823},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '4': {'participantId': 4,
      'position': {'x': 8399, 'y': 5633},
      'currentGold': 20,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '5': {'participantId': 5,
      'position': {'x': 6085, 'y': 6322},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '6': {'participantId': 6,
      'position': {'x': 9796, 'y': 6399},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '7': {'participantId': 7,
      'position': {'x': 10999, 'y': 5287},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '8': {'participantId': 8,
      'position': {'x': 8730, 'y': 8736},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '9': {'participantId': 9,
      'position': {'x': 3904, 'y': 13502},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0},
     '10': {'participantId': 10,
      'position': {'x': 10543, 'y': 5267},
      'currentGold': 0,
      'totalGold': 500,
      'level': 1,
      'xp': 0,
      'minionsKilled': 0,
      'jungleMinionsKilled': 0,
      'dominionScore': 0,
      'teamScore': 0}}




```python
match_data['frames'][1]['events']
```




    [{'type': 'ITEM_PURCHASED',
      'timestamp': 3270,
      'participantId': 7,
      'itemId': 3854},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 3633,
      'participantId': 7,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 3831,
      'participantId': 3,
      'itemId': 1054},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 3930,
      'participantId': 7,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 4194,
      'participantId': 3,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 4425,
      'participantId': 3,
      'itemId': 3340},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 4524,
      'participantId': 7,
      'itemId': 3340},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 4623,
      'participantId': 9,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 4722,
      'participantId': 6,
      'itemId': 1041},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 6372,
      'participantId': 9,
      'itemId': 1054},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 6438,
      'participantId': 6,
      'itemId': 2031},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 6537,
      'participantId': 10,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 6669,
      'participantId': 7,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 6834,
      'participantId': 6,
      'itemId': 3340},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 6900,
      'participantId': 9,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 7461,
      'participantId': 9,
      'itemId': 3340},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 8088,
      'participantId': 1,
      'itemId': 3854},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 8715,
      'participantId': 1,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 8880,
      'participantId': 1,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 9276,
      'participantId': 1,
      'itemId': 3340},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 9474,
      'participantId': 3,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 10035,
      'participantId': 10,
      'itemId': 1055},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 11388,
      'participantId': 2,
      'itemId': 1041},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 11751,
      'participantId': 2,
      'itemId': 2031},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 11883,
      'participantId': 6,
      'skillSlot': 2,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 12114,
      'participantId': 2,
      'itemId': 3340},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 13116,
      'participantId': 5,
      'itemId': 3340},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 13314,
      'participantId': 5,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 13545,
      'participantId': 5,
      'itemId': 1054},
     {'type': 'ITEM_UNDO',
      'timestamp': 14568,
      'participantId': 10,
      'afterId': 0,
      'beforeId': 1055},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 17043,
      'participantId': 10,
      'itemId': 1054},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 17703,
      'participantId': 10,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 18462,
      'participantId': 10,
      'itemId': 3340},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 19750,
      'participantId': 2,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 20674,
      'participantId': 4,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 20839,
      'participantId': 4,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 21202,
      'participantId': 4,
      'itemId': 1056},
     {'type': 'ITEM_UNDO',
      'timestamp': 24172,
      'participantId': 4,
      'afterId': 0,
      'beforeId': 1056},
     {'type': 'ITEM_UNDO',
      'timestamp': 24304,
      'participantId': 4,
      'afterId': 0,
      'beforeId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 26218,
      'participantId': 8,
      'itemId': 1055},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 26745,
      'participantId': 8,
      'itemId': 3340},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 27141,
      'participantId': 4,
      'itemId': 1082},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 27240,
      'participantId': 8,
      'itemId': 2003},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 31299,
      'participantId': 8,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_SOLD', 'timestamp': 33774, 'participantId': 4, 'itemId': 2003},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 34269,
      'participantId': 1,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 37041,
      'participantId': 4,
      'itemId': 2003},
     {'type': 'ITEM_PURCHASED',
      'timestamp': 37866,
      'participantId': 4,
      'itemId': 2003},
     {'type': 'WARD_PLACED',
      'timestamp': 47474,
      'wardType': 'UNDEFINED',
      'creatorId': 4},
     {'type': 'SKILL_LEVEL_UP',
      'timestamp': 55493,
      'participantId': 4,
      'skillSlot': 1,
      'levelUpType': 'NORMAL'}]




```python

```
