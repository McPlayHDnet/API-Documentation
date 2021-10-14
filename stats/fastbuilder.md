---
description: Requesting FastBuilder stats
---

# FastBuilder

{% swagger baseUrl="https://mcplayhd.net/api" path="/fastbuilder/{mode}/stats/{player}?token={token}" method="get" summary="Stats by player and mode" %}
{% swagger-description %}
Get the FastBuilder stats of a player by their 

**UUID or name**

.

\


All times are in Milliseconds.

\


If you want to get the average time you need to divide the 

**totalTime**

 by the 

**wins**
{% endswagger-description %}

{% swagger-parameter in="path" name="mode" type="string" %}
mode you want to get the stats of
{% endswagger-parameter %}

{% swagger-parameter in="path" name="player" type="string" %}
either the name or the UUID of the player
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-response status="200" description="Response if the player has played the specific game mode" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : { 
    "playerInfo" : {
      "uuid" : "<string - UUID of the player>",
      "name" : "<string - name of the player>",
      "group" : "<string - group of the player>"
    },
    "stats" : {
      "games" : <int - games played>,
      "wins" : <int - games won>,
      "blocks" : <long - blocks placed>,
      "timeBest" : <long - best time>,
      "timeTotal" : <long - total time of all wins>,
      "confirmed" : <boolean - if best time is confirmed>,
      "speedrunConfirmed" : <boolean - if best time is speedrun confirmed>
    }
  }
}
```
{% endswagger-response %}

{% swagger-response status="204" description="Response if the player has not played the specific game mode" %}
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

{% swagger baseUrl="https://mcplayhd.net/api" path="/fastbuilder/{mode}/top?token={token}" method="get" summary="Top stats of mode" %}
{% swagger-description %}
Returns a map of top FastBuilder players by 

**mode**

 as 

**[rank, statsObject]**
{% endswagger-description %}

{% swagger-parameter in="path" name="mode" type="string" %}
mode you want to get the stats of
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
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
          "games" : <int - games played>,
          "wins" : <int - games won>,
          "blocks" : <long - blocks placed>,
          "timeBest" : <long - best time>,
          "timeTotal" : <long - total time of all wins>,
          "confirmed" : <boolean - if best time is confirmed>,
          "speedrunConfirmed" : <boolean - if best time is speedrun confirmed>
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

{% swagger baseUrl="https://mcplayhd.net/api" path="/fastbuilder/stats?token={token}" method="get" summary="Global stats" %}
{% swagger-description %}
Returns the sum of all games, wins and blocks placed in FastBuilder.
{% endswagger-description %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "games" : <long - total games played>,
    "wins" : <long - total wins>,
    "blocks" : <long - total blocks placed>
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% swagger baseUrl="https://mcplayhd.net/api" path="/fastbuilder/stats/{player}?token={token}" method="get" summary="Global stats of player" %}
{% swagger-description %}
Returns the sum of all games, wins and blocks placed in FastBuilder by a player.
{% endswagger-description %}

{% swagger-parameter in="path" name="player" type="string" %}
either the name or the UUID of the player
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "games" : <long - total games played>,
    "wins" : <long - total wins>,
    "blocks" : <long - total blocks placed>
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
This action costs **2** rate requests.
{% endhint %}

{% swagger baseUrl="https://mcplayhd.net/api" path="/fastbuilder/{mode}/stats?token={token}" method="get" summary="Global stats of mode" %}
{% swagger-description %}
Returns the sum of all games, wins and blocks placed in a certain FastBuilder mode.
{% endswagger-description %}

{% swagger-parameter in="path" name="mode" type="string" %}
mode you want to get the stats from
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
your authentication token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "sums" : {
      "games" : <long - total games played>,
      "wins" : <long - total wins>,
      "blocks" : <long - total blocks placed>
    },
    "maxConfirmedTime" : <long - max time that will have to be confirmed until showing up in the chart>,
    "distribution" : {
      <map[long, int] - [best time, amount of players]>
    }
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% swagger baseUrl="https://mcplayhd.net/api" path="/fastbuilder/modes" method="get" summary="List of modes" %}
{% swagger-description %}
Get a list of all FastBuilder modes
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "modes" : [ "<string[] - list of modes>" ]
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
This action costs **0** rate requests.
{% endhint %}
