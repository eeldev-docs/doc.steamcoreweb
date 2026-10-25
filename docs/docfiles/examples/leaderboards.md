---
sidebar_position: 2
description: Find a Steam leaderboard and read its entries with the SteamCoreWeb plugin.
---

# Leaderboards

The **Web Leaderboards** subsystem wraps Valve's [ISteamLeaderboards](https://partner.steamgames.com/doc/webapi/ISteamLeaderboards) interface. All functions need your publisher key.

## Read the entries of a leaderboard
1. Call **Find Or Create Leaderboard** with the leaderboard's **Name**. Turn on **Create If Not Found** to create it if it doesn't exist.
2. Read the leaderboard ID from the response with **Find Json Number** and the key `leaderboardID`.
3. Call **Get Leaderboard Entries** with the ID, and a range with **Range Start** and **Range End**.
4. Read the entries with **Find Json Numbers** for `rank` and `score`, and **Find Json Strings** for `steamid`. The arrays are in the same order, so index `0` in each array belongs to the same entry.

![Find a leaderboard and read its entries](/img/leaderboards-1.png)

**Data Request** selects which entries are returned:

| Value | Entries |
|---|---|
| `0` | Global, by rank between **Range Start** and **Range End** |
| `1` | Around the player in **Steam ID**. The range is relative to the player, for example `-5` to `5`. |
| `2` | The friends of the player in **Steam ID** |

You can then show the entries in a widget:

![Leaderboard entries in a widget](/img/leaderboards-2.png)

## Set a score
Call **Set Leaderboard Score** with the leaderboard ID, the player's Steam ID and the score. **Score Method** is `KeepBest` to keep the player's best score, or `ForceUpdate` to always replace it.

:::warning
Only set scores from your server. A client that can call **Set Leaderboard Score** can post any score. See [Publisher Key Security](/docfiles/concepts/key-security).
:::

## Other functions
| Function | Description |
|---|---|
| Get Leaderboards For Game | Lists all leaderboards of the app. |
| Reset Leaderboard | Removes all entries from a leaderboard. |
| Delete Leaderboard | Deletes a leaderboard. |
