---
description: Requesting Minesweeper stats
---

# Minesweeper

{% swagger src="../.gitbook/assets/api-docs.json" path="/minesweeper/stats/{player}" method="get" %}
[api-docs.json](../.gitbook/assets/api-docs.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/api-docs.json" path="/minesweeper/stats/{player}/all" method="get" %}
[api-docs.json](../.gitbook/assets/api-docs.json)
{% endswagger %}

{% hint style="warning" %}
Requesting "all" season stats of a player costs **{season-1}** rate requests.
{% endhint %}

{% swagger src="../.gitbook/assets/api-docs.json" path="/minesweeper/top" method="get" %}
[api-docs.json](../.gitbook/assets/api-docs.json)
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% swagger src="../.gitbook/assets/api-docs.json" path="/minesweeper/stats" method="get" %}
[api-docs.json](../.gitbook/assets/api-docs.json)
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% swagger src="../.gitbook/assets/api-docs.json" path="/minesweeper/season" method="get" %}
[api-docs.json](../.gitbook/assets/api-docs.json)
{% endswagger %}

{% hint style="info" %}
These stats will update every **10** seconds.
{% endhint %}

{% hint style="warning" %}
This action costs **0** rate requests and doesn't require authentication.
{% endhint %}
