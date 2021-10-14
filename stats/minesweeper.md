---
description: Requesting Minesweeper stats
---

# Minesweeper

{% swagger baseUrl="https://mcplayhd.net/api" path="/minesweeper/stats/{player}?token={token}&season={season}" method="get" summary="Stats by player (and season)" %}
{% swagger-description %}
Get the Minesweeper stats of a player by their 

**UUID or name**

.

\


All thes are in Milliseconds.

\


If you want to get the acerage time you need to divide the 

**totalTime **

by the 

**wins**

.

\




\


You don't need to provide a specific 

**season**

. If you don't specify the 

**season**

, the API will return the players stats of the 

**current season**

.
{% endswagger-description %}

{% swagger-parameter in="path" name="player" type="string" %}
either the name or the UUID of the player
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="season" type="string" %}
number of the season ["1", "2", ...] or ["-1","all"] for a sum of games, wins and mines found 
{% endswagger-parameter %}

{% swagger-response status="200" description="Response if the player has stats in that season." %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : { # will be null if the player has not played this game
    "playerInfo" : {
      "uuid" : "<string - UUID of the player>",
      "name" : "<string - name of the player>",
      "group" : "<string - group of the player>"
    },
    "stats" : {
      "rank" : <int - rank of the player>,
      "points" : <int - points this season>,
      "timeBest" : <long - best time>,
      "timeTotal" : <long - total time of all wins>,
      "games" : <int - games played>,
      "wins" : <int - games won>,
      "mines" : <int - mines defused>
    }
  }
}
```
{% endswagger-response %}

{% swagger-response status="204" description="Response if the player has no stats in that season." %}
```yaml
{
  "status" : 204,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "playerInfo" : {
      "uuid" : "<string - UUID of the player>",
      "name" : "<string - name of the player>",
      "group" : "<string - group of the player>"
    },
    "stats" : null
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
Requesting "all" season stats of a player costs **2** rate requests.
{% endhint %}

{% swagger baseUrl="https://mcplayhd.net/api" path="/minesweeper/top?token={token}&season={season}" method="get" summary="Top stats (of season)" %}
{% swagger-description %}
Returns a map of top Minesweeper players of a certain season as 

**[rank, statsObject]**

\


****

\


****

You don't need to provide a specific 

**season**

. If you don't specify the 

**season**

, the API will return the top player map of the 

**current season**

.
{% endswagger-description %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="season" type="string" %}
number of the season ["1", "2", ...]
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "top" : {
      "1" : {
        "playerInfo" : {
          "uuid" : "<string - UUID of the player>",
          "name" : "<string - name of the player>",
          "group" : "<string - group of the player>"
        },
        "stats" : {
          "rank" : <int - rank of the player>,
          "points" : <int - points this season>,
          "timeBest" : <long - best time>,
          "timeTotal" : <long - total time of all wins>,
          "games" : <int - games played>,
          "wins" : <int - games won>,
          "mines" : <int - mines defused>
        }
      },
      "2" : {
        # Same as above
      },
      # Many more of the above
    }
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% swagger baseUrl="https://mcplayhd.net/api" path="/minesweeper/stats?token={token}&season={season}" method="get" summary="Global stats (and of season)" %}
{% swagger-description %}
Returns the sum of all games, wins and mines defused in Minesweeper.

\




\


You don't need to provide a specific 

**season**

. If you don't specify the 

**season**

, the API will return the sum of 

**all seasons**

.
{% endswagger-description %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="season" type="string" %}
number of the season ["1", "2", ...] or ["-1", "all"] for the sum of all seasons
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "games" : <int - games played>,
    "wins" : <int - games won>,
    "mines" : <int - mines defused>
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% swagger baseUrl="https://mcplayhd.net/api" path="/minesweeper/season" method="get" summary="Current season" %}
{% swagger-description %}
Get the current Minesweeper season
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "season" : <int - current season>
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% hint style="warning" %}
This action costs **0** rate requests.
{% endhint %}
