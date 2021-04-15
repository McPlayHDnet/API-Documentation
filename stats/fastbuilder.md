---
description: Requesting FastBuilder stats
---

# FastBuilder

{% api-method method="get" host="https://mcplayhd.net/api" path="/fastbuilder/{mode}/player/{player}" %}
{% api-method-summary %}
Get stats by UUID or Name
{% endapi-method-summary %}

{% api-method-description %}
Get the FastBuilder stats of a player by their **UUID or Name**.  
All times are in Milliseconds.  
If you want to get the average time you need to divide the **totalTime** by the **wins**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="mode" type="string" required=true %}
FastBuilder mode you want to get the stats of.
{% endapi-method-parameter %}

{% api-method-parameter name="player" type="string" required=true %}
Either the name or the UUID of the player.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
Your authentication token.
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
  "data" : { # will be null if the player has not played this game
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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



