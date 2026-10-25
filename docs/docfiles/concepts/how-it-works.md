---
sidebar_position: 1
sidebar_label: How Requests Work
description: How the SteamCoreWeb plugin builds and sends Steam Web API requests, and how the callback is called.
---

# How Requests Work

## From call to callback
1. You call a function, for example **Get Player Summaries**.
2. The plugin creates a task and puts it in a queue. The task runs on a separate thread, so your game thread is never blocked.
3. The task builds the request and sends it with Unreal's HTTP module.
4. When Steam responds, or the request times out, the callback is called on the **game thread**. You can update widgets and actors directly from it.

## How a request is built
Each function knows its interface, method, version and HTTP verb. The request goes to:

```
https://<host>/<Interface>/<Method>/v<Version>/
```

- **Host**: `partner.steam-api.com` for publisher calls, `api.steampowered.com` for public calls.
- **GET** requests put the parameters in the URL.
- **POST** requests send the parameters in the request body as `application/x-www-form-urlencoded`, so the key is not part of the URL.
- All values are URL encoded, so text with spaces, `&`, `+` and other characters reaches Steam as it is.
- Arrays are sent the way Steam expects them, for example `publishedfileids[0]=...&publishedfileids[1]=...` together with a count.
- Service interfaces, such as `IPublishedFileService` and `IInventoryService`, receive their parameters as `input_json` where Steam needs it.

## Timeouts
If Steam doesn't respond within **Async Task Timeout** seconds, the task is cancelled and the callback is called with **Was Successful** false. The default is 15 seconds. See [Settings](/docfiles/reference/settings).

## Debugging requests
- **Debugging** logs the verb, URL and parameters of every request, and the response.
- **Dev Mode** logs the requests without sending them.

The key is always masked as `key=***` in the log. The log category is `SteamCoreWebLog`, so you can turn on more output with:

```ini
[Core.Log]
SteamCoreWebLog=Verbose
```
