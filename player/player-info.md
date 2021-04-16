---
description: Requesting general player information
---

# Player Info

{% api-method method="get" host="https://mcplayhd.net/api" path="/player/{player}" %}
{% api-method-summary %}
Player Info
{% endapi-method-summary %}

{% api-method-description %}
Get the player information object of a player by its **UUID or name**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="player" type="string" required=true %}
either the name or the UUID of the play
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
your authentication token
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
    "uuid" : "<string - UUID of the player>",
    "name" : "<string - name of the player>",
    "group" : "<string - group of the player>"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



