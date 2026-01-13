# Hytale Server Egg

![GitHub License](https://img.shields.io/github/license/NATroutter/egg-hytale?style=for-the-badge) ![GitHub Issues](https://img.shields.io/github/issues/NATroutter/egg-hytale?style=for-the-badge)
![GitHub Stars](https://img.shields.io/github/stars/NATroutter/egg-hytale?style=for-the-badge) ![GitHub Forks](https://img.shields.io/github/forks/NATroutter/egg-hytale?style=for-the-badge)

Panel eggs for hosting Hytale game servers on both Pelican and Pterodactyl panels.

## Overview

This egg provides an automated installation and startup configuration for Hytale servers. It handles downloading the Hytale server files, setting up the environment, and starting the server with customizable parameters.

Both Pelican Panel and Pterodactyl Panel are fully supported with dedicated egg files for each platform.

> [!WARNING]
> **Server Status Reporting**: There is currently one known issue where the panel does not correctly detect when the server has started. This is because the "Start configuration" cannot be properly configured yet - the official Hytale server files have not been publicly released. Once the server files are available, this will be fixed immediately. The egg itself works perfectly fine; it just doesn't report the server status correctly to the panel.

## Features

- Automated Hytale server installation
- Automatic download of server files from official sources
- Configurable server parameters
- Easy setup and deployment
- Support for custom asset packs
- Backup management
- Multiple authentication modes

## Installation

### Pelican Panel

1. Download the [egg-hytale.pelican.json](egg-hytale.pelican.json) file from this repository
2. In your Pelican Panel, navigate to **Admin Panel** > **Eggs**
3. Click **Import**
4. Select the downloaded JSON file
5. Configure the egg settings as needed

### Pterodactyl Panel

1. Download the [egg-hytale.pterodactyl.json](egg-hytale.pterodactyl.json) file from this repository
2. In your Pterodactyl Panel, navigate to **Admin Panel** > **Nests**
3. Select or create a nest for the egg
4. Click **Import Egg**
5. Select the downloaded JSON file
6. Configure the egg settings as needed

## Server Configuration

The following variables can be configured:

| Variable | Description | Default |
| ---------- | ------------- | --------- |
| `GAME_PROFILE` | Hytale profile username for server authentication. Visit [accounts.hytale.com](https://accounts.hytale.com/) → Game Profiles to find your username. Leave empty to use first profile. | (empty) |
| `ASSET_PACK` | Assets pack (.zip) that are being send to player | `Assets.zip` |
| `ACCEPT_EARLY_PLUGINS` | Acknowledge that loading early plugins is unsupported and may cause stability issues | `false` |
| `ALLOW_OP` | Do you wish to allow operators or not | `true` |
| `AUTH_MODE` | Authentication mode (authenticated or offline) | `authenticated` |
| `AUTOMATIC_UPDATE` | Update the hytale server automatically | `true` |
| `JVM_ARGS` | Additional Java Virtual Machine arguments for advanced configuration. | See egg config |
| `LEVERAGE_AHEAD_OF_TIME_CACHE` | The server ships with a pre-trained AOT cache (HytaleServer.aot) that improves boot times by skipping JIT warmup | `true` |
| `DISABLE_SENTRY` | Disable Sentry during active plugin development. Hytale uses Sentry to track crashes. Disable it to avoid submitting your development errors | `true` |
| `ENABLE_BACKUPS` | Enable automatic backups | `false` |
| `BACKUP_DIRECTORY` | Directory where backups are saved | `/backup` |
| `BACKUP_FREQUENCY` | Backup interval in minutes | `30` |

### First-Time Authentication

During the first installation, the Hytale downloader will require authentication with your Hytale account. You'll see output similar to this in the console:

```txt
Please visit the following URL to authenticate:
https://oauth.accounts.hytale.com/oauth2/device/verify?user_code=XXXXXXXX
Or visit the following URL and enter the code:
https://oauth.accounts.hytale.com/oauth2/device/verify
Authorization code: XXXXXXXX
```

**To complete authentication:**

1. Open the provided URL in your web browser
2. Enter the authorization code shown in the console
3. Sign in with your Hytale account credentials
4. Authorize the server to download game files
5. Return to the console - the download will continue automatically

This authentication step is only required during initial setup. Subsequent server starts will not require re-authentication.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Hytale team for the game and server software
- Pelican Panel and Pterodactyl Panel for the hosting platforms
- Community contributors

## Links

- [Hytale Official Website](https://hytale.com/)
- [Pelican Panel](https://pelican.dev/)
- [Pterodactyl Panel](https://pterodactyl.io/)
- [Report Issues](https://github.com/NATroutter/egg-hytale/issues)

## Support

If you encounter any issues or have questions:

- Check existing issues for solutions
- Open an issue on GitHub

---

**Note**: This is an unofficial community-created egg and is not officially supported by Hypixel Studios or the Hytale team.
