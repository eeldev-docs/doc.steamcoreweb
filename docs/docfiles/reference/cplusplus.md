---
sidebar_position: 4
sidebar_label: C++ API
description: Use the SteamCoreWeb plugin from C++.
---

# C++ API

Add the module to your `.Build.cs`:

```csharp
PrivateDependencyModuleNames.AddRange(new string[] { "SteamCoreWeb" });
```

## Calling a function
Get the subsystem from the Game Instance and call the function. The callback is a dynamic delegate, so bind it to a `UFUNCTION`.

```cpp
#include "SteamUser/WebSteamUser.h"
#include "SteamCoreWeb/SteamWebUtilities.h"

void UMyFriendsComponent::RequestPlayerSummaries(const TArray<FString>& SteamIds)
{
	UWebSteamUser* SteamUser = GetWorld()->GetGameInstance()->GetSubsystem<UWebSteamUser>();
	if (!SteamUser)
	{
		return;
	}

	FOnSteamCoreWebCallback Callback;
	Callback.BindUFunction(this, GET_FUNCTION_NAME_CHECKED(UMyFriendsComponent, OnPlayerSummaries));

	SteamUser->GetPlayerSummaries(Callback, USteamWebUtilities::GetProjectKey(), SteamIds);
}

void UMyFriendsComponent::OnPlayerSummaries(const FString& Data, bool bWasSuccessful)
{
	if (!bWasSuccessful)
	{
		return;
	}

	TArray<FString> Names;
	ESteamJsonResult Result;
	USteamWebUtilities::FindJsonStrings(Data, TEXT("personaname"), Names, Result);
}
```

Declare the callback as a `UFUNCTION`:

```cpp
UFUNCTION()
void OnPlayerSummaries(const FString& Data, bool bWasSuccessful);
```

The callback is called on the game thread. If the object is destroyed before Steam responds, the callback is not called.

## Parsing the response with Unreal's JSON module
For more control than the JSON helpers give, parse **Data** with Unreal's JSON module. Add `"Json"` to your `.Build.cs` as well.

```cpp
#include "Dom/JsonObject.h"
#include "Serialization/JsonReader.h"
#include "Serialization/JsonSerializer.h"

TSharedPtr<FJsonObject> Root;
const TSharedRef<TJsonReader<>> Reader = TJsonReaderFactory<>::Create(Data);

if (FJsonSerializer::Deserialize(Reader, Root) && Root.IsValid())
{
	const TSharedPtr<FJsonObject>* Response;
	if (Root->TryGetObjectField(TEXT("response"), Response))
	{
		const TArray<TSharedPtr<FJsonValue>>* Players;
		if ((*Response)->TryGetArrayField(TEXT("players"), Players))
		{
			for (const TSharedPtr<FJsonValue>& Player : *Players)
			{
				const FString Name = Player->AsObject()->GetStringField(TEXT("personaname"));
			}
		}
	}
}
```

## Subsystem classes
| Class | Header |
|---|---|
| `UWebApps` | `Apps/WebApps.h` |
| `UWebBroadcastService` | `BroadcastService/WebBroadcastService.h` |
| `UWebCheatReporting` | `CheatReporting/WebCheatReporting.h` |
| `UWebEconMarketService` | `EconMarket/WebEconMarketService.h` |
| `UWebEconService` | `EconService/WebEconService.h` |
| `UWebGameInventory` | `GameInventory/WebGameInventory.h` |
| `UWebGameNotificationsService` | `GameNotificationsService/WebGameNotificationsService.h` |
| `UWebGameServersService` | `GameServersService/WebGameServersService.h` |
| `UWebInventoryService` | `InventoryService/WebInventoryService.h` |
| `UWebLeaderboards` | `Leaderboards/WebLeaderboards.h` |
| `UWebLobbyMatchmakingService` | `LobbyMatchmakingService/WebLobbyMatchmakingService.h` |
| `UWebMicroTxn` | `MicroTxn/WebMicroTxn.h` |
| `UWebPlayerService` | `PlayerService/WebPlayerService.h` |
| `UWebPublishedFileService` | `PublishedFileService/WebPublishedFileService.h` |
| `UWebSteamPublishedItemSearch` | `PublishedItemSearch/WebPublishedItemSearch.h` |
| `UWebPublishedItemVoting` | `PublishedItemVoting/WebPublishedItemVoting.h` |
| `UWebSteamCommunity` | `SteamCommunity/WebSteamCommunity.h` |
| `UWebSteamEconomy` | `SteamEconomy/WebSteamEconomy.h` |
| `UWebSteamGameServerStats` | `SteamGameServerStats/WebSteamGameServerStats.h` |
| `UWebSteamNews` | `SteamNews/WebSteamNews.h` |
| `UWebRemoteStorage` | `SteamRemoteStorage/WebRemoteStorage.h` |
| `UWebSteamUser` | `SteamUser/WebSteamUser.h` |
| `UWebSteamWebAPIUtil` | `WebAPIUtil/WebSteamWebAPIUtil.h` |
| `UWebStoreService` | `StoreService/WebStoreService.h` |
| `UWebUserAuth` | `SteamUserAuth/WebUserAuth.h` |
| `UWebUserStats` | `SteamUserStats/WebUserStats.h` |
| `UWebWishlistService` | `WishlistService/WebWishlistService.h` |
| `UWebWorkshop` | `Workshop/WebWorkshop.h` |
