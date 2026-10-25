---
sidebar_position: 3
sidebar_label: Friends List
description: Get a player's Steam friends and their names and avatars with the SteamCoreWeb plugin.
---

# Friends List

This example shows a player's Steam friends in a widget. It uses **Get Friend List** and **Get Player Summaries** from the **Web Steam User** subsystem, which wraps Valve's [ISteamUser](https://partner.steamgames.com/doc/webapi/ISteamUser) interface.

![Get friend list and player summaries](/img/friends-1.png)

## Steps
1. Call **Get Friend List** with **Get Project Key** and the player's Steam ID. While developing you can use **Get Dev Steam ID**. Set **Relationship** to `friend`, or leave it empty.
2. Get all friend IDs from the response with **Find Json Strings** and the key `steamid`. The length of the array is the number of friends.
3. Call **Get Player Summaries** with the IDs. It takes at most 100 IDs per call, so split larger lists.
4. Read the names with **Find Json Strings** and the key `personaname`, and the avatar URLs with `avatarfull`, `avatarmedium` or `avatar`.

