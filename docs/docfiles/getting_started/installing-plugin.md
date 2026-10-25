---
sidebar_position: 1
description: How to install the SteamCoreWeb plugin and move it to your project.
---

# Installing the plugin

The plugin is installed from the Epic Games Launcher.

## Locate the plugin
- Add the plugin to your library on [Fab](https://www.fab.com/listings/7e0f0b69-0b35-4652-9cff-ef32a342e433).
- In the Epic Games Launcher, open **Unreal Engine → Library → Fab Library** and search for **SteamCore Web**.

## Select Engine Version
- Click **Install to Engine** and select the engine version to install it to.

## Enable the plugin
- Open your project and go to **Edit → Plugins**.
- Search for **SteamCore Web** under **eelDev Plugins**, enable it and restart the editor.

The plugin depends on the **Online Subsystem** plugin, which is enabled automatically.

## Move the Plugin (Optional)
This step is optional, but we recommend moving installed plugins to your project's `Plugins` folder.

### Locate the plugin install location
- Locate the plugin. A common install location is:

```
C:\Program Files\Epic Games\UE_5.x\Engine\Plugins\Marketplace
```

### New location
- Move the `SteamCoreWeb` folder to your project's `Plugins` folder. Create the `Plugins` folder if it doesn't exist.

## Using the plugin from C++
If you call the plugin from C++, add the `SteamCoreWeb` module to your module's `.Build.cs`:

```csharp
PrivateDependencyModuleNames.AddRange(new string[] { "SteamCoreWeb" });
```

See [C++ API](/docfiles/reference/cplusplus) for examples.

## Next step
[Get a Web API key](/docfiles/getting_started/web-api-key).
