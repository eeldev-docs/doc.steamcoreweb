---
sidebar_position: 3
description: How to configure the SteamCoreWeb plugin in Project Settings.
---

# Configuring the plugin

The settings are in **Edit → Project Settings → Game → SteamCoreWeb Plugin**.

![SteamCoreWeb project settings](/img/settings-2.png)

## The settings you need
- **Key**: your Steamworks Web API publisher key. See [Getting a Web API Key](/docfiles/getting_started/web-api-key).
- **App ID**: your app's ID. The default is `480` (Spacewar), Valve's test app.
- **Dev Steam ID**: a Steam ID to use while developing, so you can test calls that take a Steam ID without a signed-in user.

You can read all three from Blueprints with **Get Project Key**, **Get Project App ID** and **Get Dev Steam ID**, and pass them on to the functions that need them.

![Project settings and utility functions](/img/settings-1.png)

:::warning
The settings are saved to `Config/DefaultEngine.ini`, which is packaged with your game. Leave **Key** empty in projects you ship to players, and give the key only to your server. See [Publisher Key Security](/docfiles/concepts/key-security).
:::

## Debugging
- Turn on **Debugging** to log every request the plugin sends, and the response.
- Turn on **Dev Mode** to log the requests without sending them. This is useful for checking that a request is built the way you expect.

The publisher key is masked as `key=***` in the log.

## Microtransactions
Turn on **Sandbox Mode** while you test microtransactions. The plugin then uses `ISteamMicroTxnSandbox`, which works like `ISteamMicroTxn` but no real transactions take place. See [Microtransactions](/docfiles/examples/microtransactions).

All settings are listed in [Settings](/docfiles/reference/settings).

## Next step
[Make your first call](/docfiles/getting_started/using-plugin).
