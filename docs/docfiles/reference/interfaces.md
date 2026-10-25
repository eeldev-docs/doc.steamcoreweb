---
sidebar_position: 2
sidebar_label: Supported Interfaces
description: The Steamworks Web API interfaces and functions supported by the SteamCoreWeb plugin.
---

# Supported Interfaces

Each interface is a Game Instance Subsystem with one function per Steam method. The functions are also available as async Blueprint nodes, except in Web Game Servers Service, Web Lobby Matchmaking Service, Web Published File Service and Web Steam Game Server Stats. See [Using the Plugin](/docfiles/getting_started/using-plugin). The Steam interface column links to Valve's documentation, which describes each method's parameters and response.

| Subsystem | Steam interface | Functions |
|---|---|---|
| Web Apps | [ISteamApps](https://partner.steamgames.com/doc/webapi/ISteamApps) | Get App Betas, Get App Builds, Get App Depot Versions, Get App List, Get Cheating Reports, Get Players Banned, Get Server List, Get Servers At Address, Set App Build Live, Up To Date Check |
| Web Broadcast Service | [IBroadcastService](https://partner.steamgames.com/doc/webapi/IBroadcastService) | Post Game Data Frame |
| Web Cheat Reporting | [ICheatReportingService](https://partner.steamgames.com/doc/webapi/ICheatReportingService) | Report Player Cheating, Request Player Game Ban, Remove Player Game Ban, Get Cheating Reports, Report Cheat Data, Request Vac Status For User, Start Secure Multiplayer Session, End Secure Multiplayer Session |
| Web Econ Market Service | [IEconMarketService](https://partner.steamgames.com/doc/webapi/IEconMarketService) | Get Market Eligibility, Cancel App Listings For User, Get Asset ID, Get Popular |
| Web Econ Service | [IEconService](https://partner.steamgames.com/doc/webapi/IEconService) | Get Trade History, Flush Inventory Cache, Flush Asset Appearance Cache, Flush Context Cache, Get Trade Offers, Get Trade Offer, Get Trade Offers Summary, Decline Trade Offer, Cancel Trade Offer |
| Web Game Inventory | [IGameInventory](https://partner.steamgames.com/doc/webapi/IGameInventory) | Get History Command Details, Get User History, History Execute Commands, Support Get Asset History, Update Item Defs |
| Web Game Notifications Service | [IGameNotificationsService](https://partner.steamgames.com/doc/webapi/IGameNotificationsService) | Create Session, Update Session, Enumerate Sessions For App, Get Session Details For App, Request Notifications, Delete Session, Delete Session Batch |
| Web Game Servers Service | [IGameServersService](https://partner.steamgames.com/doc/webapi/IGameServersService) | Get Account List, Create Account, Set Memo, Reset Login Token, Delete Account, Get Account Public Info, Query Login Token, Set Ban Status, Get Server Steam Ids By IP, Get Server IPs By Steam Id |
| Web Inventory Service | [IInventoryService](https://partner.steamgames.com/doc/webapi/IInventoryService) | Add Item, Add Promo Item, Consume Item, Exchange Item, Get Inventory, Get Item Defs, Get Price Sheet, Consolidate, Get Quantity, Modify Items |
| Web Leaderboards | [ISteamLeaderboards](https://partner.steamgames.com/doc/webapi/ISteamLeaderboards) | Delete Leaderboard, Find Or Create Leaderboard, Get Leaderboard Entries, Get Leaderboards For Game, Reset Leaderboard, Set Leaderboard Score |
| Web Lobby Matchmaking Service | [ILobbyMatchmakingService](https://partner.steamgames.com/doc/webapi/ILobbyMatchmakingService) | Create Lobby, Remove User From Lobby |
| Web Micro Txn | [ISteamMicroTxn](https://partner.steamgames.com/doc/webapi/ISteamMicroTxn) | Adjust Agreement, Cancel Agreement, Finalize Txn, Get Report, Get User Agreement Info, Get User Info, Init Txn, Process Agreement, Query Txn, Refund Txn |
| Web Player Service | [IPlayerService](https://partner.steamgames.com/doc/webapi/IPlayerService) | Get Recently Played Games, Get Owned Games, Get Steam Level, Get Badges, Get Community Badge Progress, Is Playing Shared Game |
| Web Published File Service | [IPublishedFileService](https://partner.steamgames.com/doc/webapi/IPublishedFileService) | Query Files, Set Developer Metadata, Update Ban Status, Update Incompatible Status, Update Tags |
| Web Steam Published Item Search | [ISteamPublishedItemSearch](https://partner.steamgames.com/doc/webapi/ISteamPublishedItemSearch) | Ranked By Publication Order, Ranked By Trend, Ranked By Vote, Result Set Summary |
| Web Published Item Voting | [ISteamPublishedItemVoting](https://partner.steamgames.com/doc/webapi/ISteamPublishedItemVoting) | Item Vote Summary, User Vote Summary |
| Web Steam Community | [ISteamCommunity](https://partner.steamgames.com/doc/webapi/ISteamCommunity) | Report Abuse |
| Web Steam Economy | [ISteamEconomy](https://partner.steamgames.com/doc/webapi/ISteamEconomy) | Can Trade, Finalize Asset Transaction, Get Asset Class Info, Get Asset Prices, Get Exported Assets For User, Get Market Prices, Start Asset Transaction, Start Trade |
| Web Steam Game Server Stats | [ISteamGameServerStats](https://partner.steamgames.com/doc/webapi/ISteamGameServerStats) | Get Game Server Player Stats For Game |
| Web Steam News | [ISteamNews](https://partner.steamgames.com/doc/webapi/ISteamNews) | Get News For App, Get News For App Authed |
| Web Remote Storage | [ISteamRemoteStorage](https://partner.steamgames.com/doc/webapi/ISteamRemoteStorage) | Enumerate User Published Files, Enumerate User Subscribed Files, Get Collection Details, Get Published File Details, Get UGC File Details, Set UGC Used By GC, Subscribe Published File, Unsubscribe Published File |
| Web Steam User | [ISteamUser](https://partner.steamgames.com/doc/webapi/ISteamUser) | Check App Ownership, Get App Price Info, Get Friend List, Get Player Bans, Get Player Summaries, Get Publisher App Ownership, Get Publisher App Ownership Changes, Get User Group List, Grant Package, Resolve Vanity URL |
| Web User Auth | [ISteamUserAuth](https://partner.steamgames.com/doc/webapi/ISteamUserAuth) | Authenticate User, Authenticate User Ticket |
| Web User Stats | [ISteamUserStats](https://partner.steamgames.com/doc/webapi/ISteamUserStats) | Get Global Achievement Percentages For App, Get Global Stats For Game, Get Number Of Current Players, Get Player Achievements, Get Schema For Game, Get User Stats For Game, Set User Stats For Game |

## Methods removed by Steam
Valve has removed some methods from the Web API. The functions are still in the plugin, but Steam answers with `404 Not Found`:

| Function | Replacement |
|---|---|
| Web Apps → Get App List (`ISteamApps/GetAppList`) | [IStoreService/GetAppList](https://partner.steamgames.com/doc/webapi/IStoreService), which needs a key |
| Web Remote Storage → Enumerate User Published Files | **Query Files** in Web Published File Service |
