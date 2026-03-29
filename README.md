# Ultimate Map Manager

A Procon plugin for managing map rotations based on player count, time of day, and day of week. Supports BF3, BF4, BF Hardline, and MOHW.

**Author:** falcontx
**License:** GPLv3

## Features

- **Player-count-based map lists** -- Automatically switch map rotations when player counts cross configured thresholds
- **Day/time scheduling** -- Restrict map lists to specific days of the week/month and time windows
- **Server name per rotation** -- Change the server name to match the active map list
- **Game presets** -- Set Normal, Hardcore, Infantry Only, or custom presets per map
- **Post-load presets** -- Send additional preset commands after each level loads
- **Map list start options** -- Start from first map, random map, continue from last played, or fully randomize
- **xVotemap compatibility** -- Preserves voted maps when switching between map lists
- **In-game admin commands** -- Enable/disable map lists and check status via `@maplist`

## Installation

1. Download the latest release from the [Releases](../../releases) page
2. Extract `CUltimateMapManager.cs` to your Procon plugins directory for the appropriate game:
   - BF3: `Plugins/BF3/`
   - BF4: `Plugins/BF4/`
   - BFHL: `Plugins/BFHL/`
   - MOHW: `Plugins/MOHW/`
3. Restart Procon or reload plugins

## Configuration

1. Set **Enable map list manager** to **No** before making changes
2. Create map lists using **Add a new map list**
3. Configure player count ranges, maps, game modes, and rounds for each list
4. Optionally enable day/time restrictions, server name changes, and presets
5. Set **Enable map list manager** to **Yes** to activate

## Admin Commands

Requires **Enable in-game admin commands** and **Change current map functions** access in Procon.

| Command | Description |
|---------|-------------|
| `@maplist` | Shows the currently active map list |
| `@maplist [index]` | Shows the status of a specific map list |
| `@maplist all` | Shows the status of all map lists |
| `@maplist [index] on` | Enables the specified map list |
| `@maplist [index] off` | Disables the specified map list |

## Recommended Companion Plugins

- **xVotemap** -- Map voting (v1.2.1+ for full compatibility)
- **Automatic Round Restarter** -- Map cycling and restart when server is empty

## Development

See [CLAUDE.md](CLAUDE.md) for architecture and development details.
