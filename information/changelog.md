---
description: Important changes will be listed here
---

# Changelog

## 0.1.0 - 2022/05/14

### Added

* BedWars API endpoint.
* Swagger-UI found at [https://mcplayhd.net/api/v1/swagger-ui/index.html](https://mcplayhd.net/api/v1/swagger-ui/index.html)

### Changed

* The API's endpoint now is [https://mcplayhd.net/api/v1/](https://mcplayhd.net/api/v1/). This will allow me to push new versions but let the old version stay online when significant changes to the existing nodes are made without everyone immediately having to update their programs.\
  _The old endpoint_ [_https://mcplayhd.net/api/_](https://mcplayhd.net/api/) _will continue working for some time but will most likely be dropped once the full release of the API comes out. I highly suggest you to switch to `/api/v1/` as soon as possible._
* Changed the way authentication is made. You should/can no longer provide your token in the URL as a parameter but should switch to using the header for providing your token.\
  If you are using Java's `HttpsURLConnection` for example, this would look like the following: \
  `connection.addRequestProperty("Authorization", "Bearer {token}");`\
  _For all the endpoints that existed before this update, the old authentication will still work until at the latest when the full release of the API comes out._
* Getting the summed stats of all seasons of a player is no longer done by providing `season="-1"` or `season="all"` but is now done by simply calling `/stats/{player}/all`. This request no longer costs a fixed 2 requests but now costs `min(1, season - 1)` requests.
* The `TopStats` is no longer a `Map<Integer, Stats>` but is now a `List<Stats>` for all modes that have top stats.
* The endpoint `/fastbuilder/stats/{player}` now also returns both the player info and the global stats of the player instead of only the global stats.

## 0.0.10 - 2021/08/11

### Changed

* If a player has not played a specific mode yet but the player exists the response code will still be 204 but the "data" will now return the "playerInfo" object. Just the "stats" object will be "null".

## 0.0.9 - 2021/06/18

### Changed

* If a request returns "null" as data (e.g. the player has been on the server but has never played that specific game you are requesting their stats) then the status of the request will be "204 - No Content" in order to avoid NullPointerException's in your code by simply asking if the status is 204.

## 0.0.8 - 2021/05/20

### Changed

* Minesweeper "Global stats (and of season)" will no longer return the season in the body because you have to specify the season as path variable if you want to get a specific season and therefore the information is unnecessary.

### Fixed

* I was able to restore the "mines" defused in season 1.

## 0.0.7 - 2021/05/19

### Added

* Minesweeper statistics

## 0.0.6 - 2021/04/16

### Added

* You can now request players information.

### Fixed

* If there are two or more players with the same name in the Database (yes, that can happen and is totally fine) the API will fetch the new names of all players and return the correct one (if there still is a player with that name after the cleanup).
* The Top-Player updater would still use the main MySQL connection resulting in a regular lag of 0.5s every 10 seconds.

## 0.0.5 - 2021/04/16

### Added

* Global mode stats will now also feature a distribution map of best times and amount of players with that best time. Note that all players with best times below `maxConfirmedTime` won't show up in this distribution unless they get confirmed.

### Changed

* All global stats as mode stats and top stats are now cached and will only update every 10 seconds but therefore they will only cost one rate request.

### Fixed

* Top-Board for Short would show up but this should not happen because we don't officially confirm times in Short.

## 0.0.4 - 2021/04/15

### Added

* `processTime` to the response
* FastBuilder modes list, global mode stats, global stats, global player stats

### Changed

* Path to FastBuilder API from `/stats/fastbuilder` to solely `fastbuilder`&#x20;

## 0.0.3 - 2021/04/15

### Added

* FastBuilder top pages

## 0.0.2 - 2021/04/15

### Added

* FastBuilder player stats

## 0.0.1 - 2021/04/14

### Added

* Main page [https://mcplayhd.net/api/](https://mcplayhd.net/api/)
* Token authentication **?token={token}**

