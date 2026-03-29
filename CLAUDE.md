# CUltimateMapManager -- Procon v2 Plugin

## Project Overview

CUltimateMapManager is a C# map rotation management plugin for Procon v2 (Battlefield game server administration). It manages map lists based on player count, time of day, and day of week. The legacy Procon v1 version lives on the `legacy` branch.

- **Language:** C#
- **License:** GPLv3
- **Author:** falcontx
- **Supported games:** BF3, BF4, BFHL, MOHW
- **Dependencies:** None (Procon v2 runtime only)

## Architecture

The plugin is a single file: `src/CUltimateMapManager.cs`. It contains:

- **`CUltimateMapManager`** -- Main plugin class extending `PRoConPluginAPI` implementing `IPRoConPluginInterface`
- **`MaplistConfig`** -- Inner class representing a map list configuration (player count range, day/time restrictions, maps)
- **`MaplistConfig.MaplistInfo`** -- Inner class representing a single map entry (game mode, filename, rounds, preset)
- **`TimeZoneInformation`** -- Inner class for Windows time zone handling via P/Invoke (kernel32.dll)

## Event Registrations

The plugin registers these Procon events in `OnPluginLoaded`:
- `OnLogin`, `OnListPlayers`, `OnPlayerLeft`, `OnRoundOverTeamScores`
- `OnRestartLevel`, `OnRunNextLevel`, `OnLevelLoaded`
- `OnMaplistList`, `OnServerInfo`, `OnMaplistGetMapIndices`, `OnMaplistGetRounds`, `OnMaplistSave`

## Threading Model

The plugin does not use its own threads. It uses Procon's task scheduler (`procon.protected.tasks.add`) for delayed actions:
- `CheckPlayerCount` -- deferred by 50ms after round end to avoid race conditions
- `DelayedNextRound` -- deferred after restart warning display
- `SetLoadPreset` -- deferred by 5 seconds after level load

## Key Features

- Multiple map lists with player count ranges (min/max)
- Day-of-week and time-of-day restrictions per map list
- Server name changes per map list
- Game presets per map (Normal, Hardcore, Infantry Only, custom)
- Post-level-load presets
- Map list randomization options
- xVotemap compatibility (voted map preservation across list changes)
- In-game admin commands (`@maplist`)

## Code Style

Style is enforced by `.editorconfig` and checked via `dotnet format` in CI.

**Critical conventions:**
- **Use `String`, `Int32`, `Boolean`, `Double`** -- NOT `string`, `int`, `bool`, `double`. The codebase uses explicit System type names everywhere.
- **Allman brace style** -- opening brace on its own line
- **4 spaces** for indentation, LF line endings
- **Block-scoped namespaces** (not file-scoped)
- **`using` directives outside namespace**, System usings first

## Build & CI

- `CUltimateMapManager.csproj` at root is a **CI-only artifact** for `dotnet format`. It is NOT a real build file -- Procon v2 assemblies are unavailable for compilation.
- **CI workflow** (`.github/workflows/ci.yml`): runs on push to `master` and PRs. Checks `dotnet format whitespace` and `dotnet format style --exclude-diagnostics IDE1007`.
- **Release workflow** (`.github/workflows/release.yml`): triggered by `v*` tags. Packages `.cs` files from `src/` into a zip and creates a GitHub Release.

### Running style checks locally

```bash
dotnet restore
dotnet format whitespace --verify-no-changes
dotnet format style --verify-no-changes --severity warn --exclude-diagnostics IDE1007
```

## Branch Structure

- `master` -- current development, Procon v2 only
- `legacy` -- archived Procon v1 version, no longer maintained
