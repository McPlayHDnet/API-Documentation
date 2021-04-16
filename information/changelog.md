---
description: Important changes will be listed here
---

# Changelog

## 0.0.5 - 2021/04/16

### Added

* Global mode stats will now also feature a distribution map of best times and amount of players with that best time. Note that all players with best times below `maxConfirmedTime` won't show up in this distribution unless they get confirmed.

### Changed

* All global stats as mode stats and top stats are now cached and will only update every 10 seconds but therefore they will only cost one rate request

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



