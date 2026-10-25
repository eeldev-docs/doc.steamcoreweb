---
sidebar_position: 1
slug: /
description: SteamCoreWeb is a Blueprint and C++ wrapper for the Steamworks Web API in Unreal Engine, covering leaderboards, microtransactions, inventory, users, stats, Workshop and more.
---

# Introduction

## The SteamCoreWeb Plugin
The SteamCoreWeb plugin (also known as SteamCore::Web) is a Blueprint wrapper and utility plugin for Unreal Engine. It lets you call the [Steamworks Web API](https://partner.steamgames.com/doc/webapi) from Blueprints and C++, without writing any HTTP code yourself.

Every Steam Web API interface is a Game Instance Subsystem. You call a function, the plugin sends the HTTP request on a background thread, and you get the JSON response back in a callback. The plugin includes helper nodes for reading values from the JSON.

![Project settings and utility functions](/img/overview-utilities.png)

## Features
- **24 Steam Web API interfaces**, including ISteamUser, ISteamUserStats, ISteamLeaderboards, ISteamMicroTxn, IInventoryService, IPublishedFileService and IGameServersService. See [Supported Interfaces](/docfiles/reference/interfaces).
- **Two ways to call every function**: a callback function on the subsystem, or an async Blueprint node. See [Using the Plugin](/docfiles/getting_started/using-plugin).
- **Microtransactions** with a sandbox mode, so you can test the whole purchase flow without real transactions. See [Microtransactions](/docfiles/examples/microtransactions).
- **JSON helpers** that find strings, numbers and bools in the response by key. See [Utility Functions](/docfiles/reference/utilities).
- **Project settings** for your publisher key, App ID and a development Steam ID, readable from Blueprints. See [Configuring the Plugin](/docfiles/getting_started/configuring-plugin).
- **Debug and dev mode** that print the request strings, or print them without sending anything. The publisher key is masked in the log.
- **Disable the subsystems you don't use**, so they are never created.

## Requirements
| | |
|---|---|
| Target platforms | Windows, Mac, Linux, Android |
| Steamworks | A Steamworks partner account and a Web API publisher key for the calls that need one. See [Getting a Web API Key](/docfiles/getting_started/web-api-key). |
| Unreal Engine | See the [Fab listing](https://www.fab.com/listings/7e0f0b69-0b35-4652-9cff-ef32a342e433) for the supported engine versions |

:::warning
Most Steam Web API calls need your **publisher key**. Anyone who has your key can act on behalf of your app, so never ship it in a client build. See [Publisher Key Security](/docfiles/concepts/key-security).
:::

## Where to go next
1. [Install the plugin](/docfiles/getting_started/installing-plugin)
2. [Get a Web API key](/docfiles/getting_started/web-api-key)
3. [Configure it in Project Settings](/docfiles/getting_started/configuring-plugin)
4. [Make your first call](/docfiles/getting_started/using-plugin)
