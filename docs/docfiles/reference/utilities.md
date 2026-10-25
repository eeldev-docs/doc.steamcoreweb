---
sidebar_position: 3
sidebar_label: Utility Functions
description: The JSON helpers and project setting getters in the SteamCoreWeb plugin.
---

# Utility Functions

The utility functions are in the **SteamCoreWeb → Utilities** category in Blueprints, and in `USteamWebUtilities` in C++.

## JSON helpers
Each helper has a **Found** and a **Not Found** output, so you can branch on the result directly.

| Function | Returns |
|---|---|
| Find Json String | The first string value with the key |
| Find Json Strings | Every string value with the key |
| Find Json Number | The first number value with the key, as an integer |
| Find Json Numbers | Every number value with the key, as integers |
| Find Json Bool | The first bool value with the key |
| Find Json Bools | Every bool value with the key |

- The key is not case sensitive.
- The helpers search the whole response, including nested objects and arrays.
- The value must have the right JSON type. Steam sends Steam IDs as strings, so use **Find Json String** for them, not **Find Json Number**.
- Numbers are returned as 32-bit integers. Read 64-bit values, such as Steam IDs and published file IDs, as strings.

## Project settings
| Function | Returns |
|---|---|
| Get Project Key | The publisher key from the command line, the `STEAMCOREWEB_KEY` environment variable or Project Settings, in that order. See [Publisher Key Security](/docfiles/concepts/key-security). |
| Get Project App ID | **App ID** from Project Settings |
| Get Dev Steam ID | **Dev Steam ID** from Project Settings |

## Microtransactions
| Function | Returns |
|---|---|
| Make Transaction ID | A unique 64-bit order ID for **Init Txn**, as a string. It is in the **SteamCoreWeb → MicroTxn** category. See [Microtransactions](/docfiles/examples/microtransactions). |
