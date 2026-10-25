---
sidebar_position: 2
sidebar_label: Getting a Web API Key
description: How to get a Steamworks Web API publisher key for the SteamCoreWeb plugin.
---

# Getting a Web API Key

To use the Steamworks Web API, you need your own Web API key from Valve. You can read more in Valve's documentation on [publisher keys](https://partner.steamgames.com/doc/webapi_overview/auth#publisher-keys).

## Which calls need a key
| Kind of call | Key needed | Host |
|---|---|---|
| Public calls, such as **Get Number Of Current Players**, **Get News For App** and **Get Published File Details** | No | `api.steampowered.com` |
| Calls that read user data, such as **Get Player Summaries** and **Get Owned Games** | Yes, a publisher key or a user key | `api.steampowered.com` |
| Publisher calls, such as **Check App Ownership**, **Set Leaderboard Score**, **Init Txn** and **Add Item** | Yes, a **publisher** key | `partner.steam-api.com` |

The plugin picks the right host for each function, so you don't need to set it yourself.

## Create a publisher key
1. Sign in to [Steamworks](https://partner.steamgames.com).
2. Go to **Users & Permissions → Manage Groups** and open the group for your app.
3. Create a Web API key for the group. The key is a 32 character hex string.

The key gives access to every app in the group. Keep it secret, see [Publisher Key Security](/docfiles/concepts/key-security).

:::tip
A key that Steam doesn't accept gives a `401` or `403` response for every call that needs a key. Public calls still work, so test with one of them first if you're not sure whether the problem is the key.
:::

## Next step
[Configure the plugin](/docfiles/getting_started/configuring-plugin).
