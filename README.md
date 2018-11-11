# Spotify Playlist Sensor
![header](images/header.PNG)

Home Assistant sensor that pulls the name, URI (unique request identifier), and image URL from your current Spotify playlists. Use with [Spotify Playlist Card](https://github.com/dnguyen800/Spotify-Playlist-Card) to display playlist buttons on your Lovelace UI. Requires a Spotify Premium account.

## Features
  - It works

## Options

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| name | string | **Required** | Name of the sensor, such as `playlists`.
| client_id | string | **Required** | The Spotify client ID for the Spotify app you created during instructions.
| client_secret | string | **Required** | The Spotify client secret for the Spotify app you created during instructions.
| playlists | integer | 6 | Selects the x number of recent playlists. Most recent playlists start from the top to bottom in the Spotify app.

## Instructions
1. Setup Spotify Developer account and follow directions from the Prerequisitie section of [Spotify Media Player component](https://www.home-assistant.io/components/media_player.spotify/) to create a Spotify app specifically for this sensor. Don't forget to fill out the redirect URI.
2. Do not use the same client ID and secret from your existing Spotify media player component as they may conflict.
3. Download the [spotify-playlist-sensor](https://raw.githubusercontent.com/dnguyen800/Spotify-Playlist-Sensor/master/spotify-playlist.py)
4. Place the file in your `config/custom_components/sensor` folder
5. Include the sensor in your `configuration.yaml`
```yaml
- platform: spotify-playlist
  name: "Playlists"
  client_id: 'your_id'
  client_secret: 'your_secret'
```

6. Reboot Home Assistant instance to load the sensor.
7. Check the Notifications tab in Lovelace UI to finish authorizing with Spotify
8. Locate the sensor in the Home Assistant UI, view more info and confirm your playlists are loaded.
9. (Optional) Setup the [Spotify-Playlist-Card](https://raw.githubusercontent.com/dnguyen800/Spotify-Playlist/master/spotify-playlist-card.js) to make use of this sensor.

## FAQ
- How often does the sensor refresh?

I set it to two minutes. You can change the SCAN_INTERVAL in the .py file to whatever you like.

- After I finish authorizing in the Home Assistant UI, a blank screen pops up.

## Support
I am studying Python as a hobby and this is my first public project. Some fixes/requests may be out of my scope but I'll try my best. I hope you find it useful!

## Credits
  - [Spotify Media Player Home Assistant component](https://www.home-assistant.io/components/media_player.spotify/) - I re-used the token authorization code.
  - [Feed Parser component](https://github.com/custom-components/sensor.feedparser) - Used as a starting point to write the playlist sensor. Thanks!

