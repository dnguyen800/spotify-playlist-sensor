# Spotify Playlist Sensor
Home Assistant sensor that pulls the name, URI (unique request identifier), and image URL from your current Spotify playlists. Use with [Spotify Playlist Card](https://github.com/dnguyen800/Spotify-Playlist-Card) to display playlist buttons on your Lovelace UI. Requires a Spotify Premium account.

## Features
  - It works, don't break it please.  

## Options

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| name | string | **Required** | Name of the sensor, such as `playlists`.
| client_id | string | **Required** | The Spotify client ID for the Spotify app you created earlier.
| client_secret | string | **Required** | The Spotify client secret for the Spotify app you created earlier.
| playlists | integer | 6 | Selects the x number of recent playlists. Most recent playlists start from the top to bottom in the Spotify app.
| refresh_interval | integer | 3600 | Specify the interval (in seconds) to refresh playlists.

## Instructions
1. Setup Spotify Developer account and follow directions from the Prerequisitie section of Home Assistant website(https://www.home-assistant.io/components/media_player.spotify/) to create a Spotify app specifically for this sensor. Don't forget to fill out redirect URI.
2. Do not use the same client ID and secret from your existing Spotify media player component.  They will conflict.
3. 
1. Download the [spotify-playlist-sensor]https://raw.githubusercontent.com/dnguyen800/Spotify-Playlist-Sensor/master/spotify-playlist.py)
2. Place the file in your `config/custom_components/sensor` folder
3. Include the sensor in your `configuration.yaml`
```yaml
- platform: spotifyplaylist
  name: "Playlists"
  client_id: 'your_id'
  client_secret: 'your_secret'
```

Reboot Home Assistant instance

Check Notifications tab in Lovelace UI to finish authorizing with Spotify

Find the sensor in Home Assistant and confirm your playlists are loaded.

5. (Optional) Setup the [Spotify-Playlist-Card](https://raw.githubusercontent.com/dnguyen800/Spotify-Playlist/master/spotify-playlist-card.js)


## FAQ


## Support
I am studying Python as a hobby and this is my first public project. 

## Credits
  - [Spotify media player Home Assistant component](https://www.home-assistant.io/components/media_player.spotify/) - I re-used the token authorization code.

