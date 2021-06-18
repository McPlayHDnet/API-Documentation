---
description: Important changes will be listed here
---

# Changelog

## 0.0.9 - 2021/06/18

### Changed

* If a request returns "null" as data \(e.g. the player has been on the server but has never played that specific game you are requesting their stats\) then the status of the request will be "204 - No Content" in order to avoid NullPointerException's in your code by simply asking if the status is 204.

## 0.0.8 - 2021/05/20

### Changed

* Minesweeper "Global stats \(and of season\)" will no longer return the season in the body because you have to specify the season as path variable if you want to get a specific season and therefore the information is unnecessary.

### Fixed

* I was able to restore the "mines" defused in season 1.

## 0.0.7 - 2021/05/19

### Added

* Minesweeper statistics

## 0.0.6 - 2021/04/16

### Added

* You can now request players information.

### Fixed

* If there are two or more players with the same name in the Database \(yes, that can happen and is totally fine\) the API will fetch the new names of all players and return the correct one \(if there still is a player with that name after the cleanup\).
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

* Path to FastBuilder API from `/stats/fastbuilder` to solely `fastbuilder` 

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



