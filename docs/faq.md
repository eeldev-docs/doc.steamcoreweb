---
sidebar_position: 4
sidebar_label: FAQ & Troubleshooting
description: Answers to common questions and problems with the SteamCoreWeb plugin.
---

# FAQ & Troubleshooting

## Every call returns 401 or 403
Steam doesn't accept the key. Check that:
- The key is a **publisher** key for the group that contains your app, see [Getting a Web API Key](/docfiles/getting_started/web-api-key). A user key from steamcommunity.com doesn't work for publisher calls.
- **App ID** is set to your own app, not `480`.
- The key hasn't been revoked.

Try a public call such as **Get Number Of Current Players** first. If it works, the plugin and network are fine and the problem is the key.

## A call returns 404 Not Found
Steam doesn't have the method anymore. See [Methods removed by Steam](/docfiles/reference/interfaces#methods-removed-by-steam) for the known ones and their replacements.

## Was Successful is true, but the response contains an error
**Was Successful** only tells you that Steam responded. Steam reports errors in the response, for example `"result": 2`, an `error` field or an `errordesc` field. Check the response with the [JSON helpers](/docfiles/reference/utilities).

## The callback is never called
- Check that **Dev Mode** is off. With Dev Mode on, nothing is sent to Steam.
- Check that the subsystem isn't in **Disabled Subsystems**.
- If Steam doesn't respond within **Async Task Timeout**, the callback is called with **Was Successful** false. Turn on **Debugging** to see the request in the log.

## How do I see what is sent to Steam?
Turn on **Debugging** in Project Settings. Every request and response is logged in the `SteamCoreWebLog` category. The key is masked as `key=***`. Turn on **Dev Mode** as well to log the requests without sending them.

## Find Json Number doesn't find my Steam ID
Steam sends Steam IDs and other 64-bit IDs as strings. Use **Find Json String** or **Find Json Strings** for them.

## Can I use the plugin in a shipped client?
Yes, for calls that don't need a key. Calls that need your publisher key should only run on a server you control, since a key in the client can be read by anyone with the build. See [Publisher Key Security](/docfiles/concepts/key-security).

## Do I need the Steam Online Subsystem?
No. The plugin talks to the Steam Web API over HTTP and doesn't need the Steam client or the Steamworks SDK. You need the Steamworks SDK, or a plugin like [SteamCore PRO](https://steamcore-pro.eeldev.com), for things that happen in the client, such as getting the authorization callback after **Init Txn**.

## Are microtransactions charged while I test?
Not when **Sandbox Mode** is on. Turn it off before you release. See [Microtransactions](/docfiles/examples/microtransactions).
