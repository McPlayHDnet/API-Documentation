---
description: Requesting Minesweeper stats
---

# Minesweeper

{% api-method method="get" host="https://mcplayhd.net/api" path="/minesweeper/stats/{player}?token={token}&season={season}" %}
{% api-method-summary %}
Stats by player \(and season\)
{% endapi-method-summary %}

{% api-method-description %}
Get the Minesweeper stats of a player by their **UUID or name**.  
All thes are in Milliseconds.  
If you want to get the acerage time you need to divide the **totalTime** by the **wins**.  
  
You don't need to provide a specific **season**. If you don't specify the **season**, the API will return the players stats of the **current season**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="player" type="string" required=true %}
either the name or the UUID of the player
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
your authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="season" type="string" %}
number of the season \["1", "2", ...\] or \["-1","all"\] for a sum of games, wins and mines found 
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
For **season 1**, the **mines** were not recorded. For the "all"-seasons stats we just set the number of mines defused of the first season to 0.
{% endhint %}

{% hint style="warning" %}
Requesting "all" season stats of a player costs **2** rate requests.
{% endhint %}

{% api-method method="get" host="https://mcplayhd.net/api" path="/minesweeper/top?token={token}&season={season}" %}
{% api-method-summary %}
Top stats \(of season\)
{% endapi-method-summary %}

{% api-method-description %}
Returns a map of top Minesweeper players of a certain season as **\[rank, statsObject\]**  
  
You don't need to provide a specific **season**. If you don't specify the **season**, the API will return the top player map of the **current season**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
your authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="season" type="string" required=false %}
number of the season \["1", "2", ...\]
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% api-method method="get" host="https://mcplayhd.net/api" path="/minesweeper/stats?token={token}&season={season}" %}
{% api-method-summary %}
Global stats \(and of season\)
{% endapi-method-summary %}

{% api-method-description %}
Returns the sum of all games, wins and mines defused in Minesweeper.  
  
You don't need to provide a specific **season**. If you don't specify the **season**, the API will return the sum of **all seasons**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
your authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="season" type="string" required=false %}
number of the season \["1", "2", ...\] or \["-1", "all"\] for the sum of all seasons
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
  "status" : 200,
  "path" : "<string - current path>",
  "timeStamp" : "<string - current time stamp>",
  "processingTime" : <long - time to process the action in ms>,
  "data" : {
    "season" : <int - requested season or -1 for all seasons>,
    "games" : <int - games played>,
    "wins" : <int - games won>,
    "mines" : <int - mines defused>
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
For **season 1**, the **mines** were not recorded. For the "all"-seasons stats we just set the number of mines defused of the first season to 0.
{% endhint %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% api-method method="get" host="https://mcplayhd.net/api" path="/season" %}
{% api-method-summary %}
Current season
{% endapi-method-summary %}

{% api-method-description %}
Get the current Minesweeper season
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% hint style="warning" %}
This action costs **0** rate requests.
{% endhint %}

