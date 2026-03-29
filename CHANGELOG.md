# Changelog

## v2.0.0 (2026-03-29)

Refactor for Procon v2 compatibility.

- Convert from `.inc` + game-variant stubs to single `.cs` in `src/`
- Remove `Plugins/` directory with game-variant stubs
- Convert code style to System types (`String`, `Int32`, `Boolean`, etc.)
- Add `.editorconfig`, `CUltimateMapManager.csproj` for CI format checks
- Add CI and release GitHub Actions workflows
- Add `CLAUDE.md`, `README.md`, `CHANGELOG.md`, `LICENSE`, `.gitignore`

## v1.2.5.0 (2015-03-26)

- Added support for BFHL

## v1.2.4.0 (2014-02-03)

- Added a check for external map list changes
- Added in-game commands to enable/disable map lists

## v1.2.3.6 (2013-12-11)

- Fixed secondary preset config display bug

## v1.2.3.4 (2013-12-07)

- Fixed map management bug caused by last update

## v1.2.3.2 (2013-12-07)

- Added an option to send a different preset after the level loads

## v1.2.3.0 (2013-11-26)

- Changed max server size back to 64 for BF4
- Fixed possible issue detecting next map at end of round for BF4
- Fixed 'Send preset commands after every round?' setting was appearing even when game presets were disabled

## v1.2.2.6 (2013-11-06)

- Added correct presets for BF4
- Added option to send custom preset commands between every round

## v1.2.2.4 (2013-11-05)

- Added support for up to 70 players for BF4

## v1.2.2.2 (2013-11-02)

- Fixed issues with quotes and vertical lines in presets

## v1.2.2.0 (2013-10-31)

- Added support for BF4

## v1.2.1.0 (2013-05-21)

- Added support for MOHW (custom playlists only)
- Map lists using both day and time will now switch at the specified time rather than at 0:00 when the day changes

## v1.2.0.2 (2012-08-24)

- Fixed bug with 'Change map list only after map has completed its total number of rounds' option

## v1.2.0.1 (2012-07-19)

- Removed debug code left in v1.2.0.0 by mistake

## v1.2.0.0 (2012-07-19)

- Fixed bug caused by changes in PRoCon 1.3
- Added option to yell before rotation is changed when using 'switch immediately'
- Added option to start on the same map that was just played
- Added round minimum for map lists
- Added option to change map list only after map has completed its total number of rounds
- Added option to ignore 'switch immediately' for time-based changes

## v1.1.2.6 (2012-05-14)

- Fixed time zones with commas were missing from the list
- Added option to use system time zone

## v1.1.2.5 (2012-03-30)

- More minor compatibility changes due to PRoCon/R-20 updates

## v1.1.2.4 (2012-03-29)

- Minor compatibility changes due to upcoming PRoCon/R-20 updates

## v1.1.2.3 (2012-02-19)

- Fixed time calculations were sometimes incorrect when start time was after stop time

## v1.1.2.2 (2012-02-11)

- Fixed map list names bug when '|' is attempted to be used
- Custom map names now shown in debug logs when map lists change
- Fixed time calculations weren't working properly on some systems

## v1.1.2.1 (2012-02-07)

- Fixed map list names not being saved
- Fixed bug related to sorting the time zone list on some systems

## v1.1.2.0 (2012-02-06)

- Fixed time zones greater than GMT were not being saved properly
- Improved compatibility with xVotemap
- Added list of recommended supporting plugins
- Added time-dependent map lists
- Added ability to name map lists

## v1.1.1.0 (2012-02-02)

- Added another map list check when no players are on the server
- Added option to avoid playing the same map when a new map is loaded
- Added option to start with the map in the new list that follows the one that was just played
- Added ability to randomize entire map list
- Updated map list change method

## v1.1.0.2 (2012-01-27)

- Fixed problem adding new presets after some were renamed
- New custom presets are now named based upon the template used to create them
- Fixed not starting at first map when not using 'start with random'
- Added the ability to disable map lists

## v1.1.0.1 (2012-01-20)

- Custom preset map assignments weren't being restored on restart
- Custom presets can now be renamed
- Day-dependent map lists no longer clear the options on some systems

## v1.1.0.0 (2012-01-17)

- Decreased options redraw time even more (almost instant now)
- Added custom presets
- Added day-dependent map lists

## v1.0.0.2 (2012-01-09)

- Greatly decreased load time and options redraw time with long/many map lists
- Fixed presets not always set properly or at correct time
- Presets for next map now set at end of round
- Fixed map list was not reloaded if number of rounds was changed
- Fixed map list changed too soon if 'Switch to new map immediately' was enabled

## v1.0.0.1 (2012-01-05)

- Fixed first map not set when map list changed after manual round restart
- Fixed map list would not update if changed when enabled via options panel
- Fixed wrong number of players detected when listplayers not called with 'all'

## v1.0.0.0 (2011-12-31)

- Initial version
