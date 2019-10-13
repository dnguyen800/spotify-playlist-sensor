# Spotify Playlist Sensor

[![GitHub Release][releases-shield]][releases]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE.md)

![Project Maintenance][maintenance-shield]


This is a Home Assistant Component that pulls playlist data from your Spotify accounts. To integrate with [Spotify Playlist Card][Spotify-Playlist-Card]. Requires a Spotify Premium account.

Please note I am not actively updating this sensor anymore. I recommend using [spotify-card](https://github.com/custom-cards/spotify-card) by user @fondberg for a much better Lovelace card implementation (and no need for a separate Spotify sensor). I'll update this sensor for small changes and for programming practice.


**This component will set up the following platforms.**

Platform | Description
-- | --
`sensor` | Show Spotify playlist data from Spotify user.

![header][headerimg]

## HACS Installation

1. Include this repository as a custom integration in the HACS settings.

```yaml
https://github.com/dnguyen800/spotify-playlist-sensor
```

2. If added correctly, the repository should be listed like below:

![hacs][hacs-image]

## Manual Installation

1. Access the HA config directory (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `spotify-playlist-sensor`.
4. Download _all_ the files from the `custom_components/spotify-playlist-sensor/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.

Your HA configuration directory (folder) should have the following files:

```text
custom_components/spotify-playlist-sensor/__init__.py
custom_components/spotify-playlist-sensor/manifest.json
custom_components/spotify-playlist-sensor/sensor.py
```

## Configuration
1. Setup Spotify Developer account and follow directions from the Prerequisite section of [Spotify Media Player component](https://www.home-assistant.io/components/media_player.spotify/) to create a Spotify app specifically for this sensor. Don't forget to fill out the redirect URI.

2. Add the sensor in your `configuration.yaml`
```yaml
sensor:
  - platform: spotify-playlist-sensor
    client_id: 'your_id'
    client_secret: 'your_secret'
```
3. Restart Home Assistant.
4. Check the Notifications tab in Lovelace UI to finish Spotify authorization.
5. Locate the sensor in the Home Assistant UI, view ``more info`` and confirm your playlists are loaded.
6. (Optional) Setup the [Spotify-Playlist-Card](https://github.com/dnguyen800/spotify-playlist-card) to make use of this sensor.




## Example configuration.yaml

```yaml
sensor:
  - platform: spotify-playlist-sensor
    client_id: 'your_id'
    client_secret: 'your_secret'
```


### Configuration options for `sensor` list

Key | Type | Required | Default | Description
-- | -- | -- | -- | --
`client_id` | `string` | `True` |  `test` | The Spotify client ID for the Spotify app you created during instructions.
`client_secret` | `string` | `True` | `test` | The Spotify client secret for the Spotify app you created during instructions.
`name` | `string` | `False` | `SpotifyPlaylist` | Name of the sensor, such as `playlists`.
`number_of_playlists` | `integer` | `False` | 6 | Selects the top x number of recent playlists. Most recent playlists start from the top to bottom in the Spotify app.
`offset` | `integer` | `False` | 0 | The index of the first playlist to return. Default: 0 (the first object). Maximum offset: 100.000.



## FAQ
- I previously used this sensor and I don't see my curated playlists (e.g. Discovery Weekly, Release Radar) created by others. Is this fixed?

The scope used to communicate with Spotify API was updated with release v0.1.1. Delete the `.spotifyplaylist-token-cache` and re-authenticate again to get a proper token. Thanks to user @bretteldridge for pointing this out.

- How often does the sensor refresh?

I set it to two minutes. You can change the SCAN_INTERVAL in the ``sensor.py`` file to whatever you like.

- After I finish authorizing in the Home Assistant UI, a blank screen pops up.

Authorization should be complete and the sensor should be pulling data from Spotify now.

## Support
I am studying Python as a hobby and this is my first public project. Some fixes/requests may be out of my scope but I'll try my best. I hope you find it useful!

## Credits
  - [Spotify Media Player Home Assistant component](https://www.home-assistant.io/components/media_player.spotify/) - I re-used the token authorization code.
  - [Feed Parser component](https://github.com/custom-components/sensor.feedparser) - Used as a starting point to write the playlist sensor. Thanks!
  - [Blueprint component](https://github.com/custom-components/blueprint) - Used to standardize HA component and card documentation.


## Contributions are welcome!

If you want to contribute to this please read the [Contribution guidelines](CONTRIBUTING.md)

***
[hacs-image]: images/hacs.png
[Spotify-Playlist-Card]: https://github.com/dnguyen800/Spotify-Playlist-Card
[spotify-playlist]: https://github.com/dnguyen800/Spotify-Playlist-Sensor

[commits-shield]: https://img.shields.io/github/commit-activity/y/dnguyen800/Spotify-Playlist-Sensor.svg
[commits]: https://github.com/dnguyen800/Spotify-Playlist-Sensor/releases/commits/master
[headerimg]: header.png
[license-shield]: https://img.shields.io/github/license/dnguyen800/Spotify-Playlist-Sensor.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-Dan%20Nguyen%20%40dnguyen800-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/dnguyen800/Spotify-Playlist-Sensor.svg?style=for-the-badge
[releases]: https://github.com/dnguyen800/Spotify-Playlist-Sensor/releases





