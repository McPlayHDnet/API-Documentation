---
description: Requesting general player information
---

# Player Info

{% swagger baseUrl="https://mcplayhd.net/api" path="/player/{player}" method="get" summary="Player Info" %}
{% swagger-description %}
Get the player information object of a player by its 

**UUID or name**

.
{% endswagger-description %}

{% swagger-parameter in="path" name="player" type="string" %}
either the name or the UUID of the play
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
    "uuid" : "<string - UUID of the player>",
    "name" : "<string - name of the player>",
    "group" : "<string - group of the player>"
  }
}
```
{% endswagger-response %}
{% endswagger %}

