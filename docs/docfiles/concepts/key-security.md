---
sidebar_position: 2
description: How to keep your Steamworks publisher key safe when using the SteamCoreWeb plugin.
---

# Publisher Key Security

Your publisher key gives full access to the Steam Web API for every app in its group. With it, anyone can grant items, change leaderboards, refund transactions and read your sales data. Treat it like a password.

## Don't ship the key to players
Everything in `Config/DefaultEngine.ini` is packaged with your game and can be read from the build. A key in **Project Settings → Key** is therefore readable by every player.

The plugin logs a warning on startup if a key is set in a client build.

## Keep the key on a server
Run the calls that need a publisher key on a server you control, such as a dedicated server, and let clients ask the server for the result. The server can get the key without it ever being in the project files:

| Source | Example |
|---|---|
| Command line | `MyGameServer.exe -SteamCoreWebKey=<your key>` |
| Environment variable | `STEAMCOREWEB_KEY=<your key>` |
| Project Settings | `Key=` in `[/Script/SteamCoreWeb.SteamCoreWebSettings]` |

**Get Project Key** checks them in this order and returns the first one that is set. Leave **Key** empty in Project Settings, and set the key on the server with the command line or the environment variable.

:::warning
Calls like **Add Item**, **Grant Package**, **Set Leaderboard Score** and **Init Txn** must never be triggered directly by a client. A player could otherwise give themselves items or change scores. Validate the request on your server first.
:::

## If your key has leaked
Revoke the key in Steamworks and create a new one. Requests with the old key fail with `403` once it is revoked.
