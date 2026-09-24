<div align="center">

# P3R Rainmeter Player

A Persona 3 Reload-inspired Spotify mini player for Rainmeter.

<img src="preview.gif" alt="P3R Rainmeter Player preview" width="400">

<p>
  <a href="https://github.com/sojjeoi/p3r-rainmeter-player/releases/latest"><img src="https://img.shields.io/badge/Download-.rmskin-2f9fd0?style=for-the-badge" alt="Download .rmskin"></a>
</p>

<p>
  <img src="https://img.shields.io/badge/Windows-Rainmeter-0078D6?style=flat-square" alt="Windows">
  <img src="https://img.shields.io/badge/Spotify-supported-1DB954?style=flat-square" alt="Spotify">
  <img src="https://img.shields.io/badge/status-fan--made-777777?style=flat-square" alt="Fan-made">
</p>

</div>

A lightweight desktop music player skin inspired by the portable music player UI from **Persona 3 Reload**.

It displays your current Spotify track, elapsed playback time, and provides basic media controls directly from your desktop.

## Features

- Spotify track title or artist display
- Elapsed playback time that ticks steadily once per second
- Rim buttons modeled on the original Walkman: info, play / pause, volume, previous, next
- Button name labels on hover
- 8 LCD color presets, switched from the right-click menu
- Equalizer bars that move while music is playing
- Persona 3 Reload-inspired LCD design
- Transparent desktop widget
- Always-on-top support
- Click-through support

## LCD Colors

<div align="center">
  <img src="docs/lcd-colors.png" alt="The eight LCD color presets" width="800">
</div>

Right-click the skin and pick an **LCD:** entry. The screen, text and icons change together, and the choice is kept after a restart.

To use your own colors, edit these two lines in `P3RPlayer.ini` and refresh the skin:

```ini
; Screen color (shows about 14% darker than the value)
LCDColor=150,225,227
; Text and icon color
LCDText=24,55,55,255
```

## Installation

1. Install [Rainmeter](https://www.rainmeter.net/) (4.5.16 or newer).
2. Install the [Long Pixel-7](https://font.download/font/long-pixel-7) font: extract the ZIP, right-click the `.ttf` file and select **Install**.
3. Download **P3RPlayer_v*.rmskin** from [Releases](https://github.com/sojjeoi/p3r-rainmeter-player/releases/latest), double-click it and click **Install**.

That's it. The `MediaPlayer` plugin that reads Spotify playback is included in the `.rmskin`, and the skin loads on its own. Keep [Spotify Desktop](https://www.spotify.com/download/windows/) running and play a song.

<details>
<summary>Manual install (without the .rmskin)</summary>

1. Install the [RainmeterMediaPlayer](https://github.com/i2002/RainmeterMediaPlayer/releases) plugin: download its `.rmskin`, open it and click **Install**.

2. Click **Code → Download ZIP** on this repository.

3. Extract the ZIP file.

4. Rename the extracted folder to:

```text
P3RPlayer
```

5. Move the folder to:

```text
Documents\Rainmeter\Skins\
```

The final folder structure should look like this:

```text
P3RPlayer
├── P3RPlayer.ini
└── @Resources
    └── Images
        ├── player_body.png
        ├── player_body_300.png
        └── lcd_screen.png
```

6. Open Rainmeter, click **Refresh all**, then load:

```text
P3RPlayer → P3RPlayer.ini
```

</details>

## Recommended Settings

To keep the player visible above other windows:

```text
Right-click the skin
→ Settings
→ Position
→ Stay Topmost
```

To allow mouse clicks to pass through the widget:

```text
Right-click the skin
→ Settings
→ Click through
```

> [!NOTE]
> With **Click through** enabled, the player's buttons cannot be clicked.
> Leave it off if you want to control playback from the widget.

## Controls

The buttons on the top rim, from left to right:

| Button | Action |
|---|---|
| INFO | Show the track title or the artist |
| PLAY | Play / Pause |
| VOL − / + | Windows volume down / up (5%) |
| PREV | Previous track |
| NEXT | Next track |

Hover over a button to see its name. The black cap on the left also has hidden Previous / Play / Next areas.

Right-click the skin to change the LCD color.

Spotify must be running for the playback controls to work.
The buttons do not respond while **Click through** is enabled.

## How it works

<div align="center">
  <img src="docs/architecture.png" alt="How the skin is put together" width="800">
</div>

- **Playback data:** Spotify publishes its state to the Windows media session. `MediaPlayer.dll` reads it, and the skin polls it.
- **Elapsed time:** the plugin rounds song position and wall time to whole seconds separately, so its counter skips or stalls. The skin counts on the system clock instead and resyncs only on pause, seek or track change.
- **Rim buttons:** drawn behind the body image, so only their top edge shows, like the Sony Walkman the in-game player is based on.
- **LCD colors:** the LCD is cut out of the artwork as a grey mask (`lcd_screen.png`) and tinted at runtime, so one image covers every color.

## Troubleshooting

### No player active

Make sure:

- Spotify Desktop is running
- A song is currently playing
- The skin was installed from the `.rmskin` (it includes the MediaPlayer plugin), or RainmeterMediaPlayer is installed if you installed manually

If necessary, restart Rainmeter after installing.

### The font looks different

Make sure **Long Pixel-7** is installed, then refresh the skin.

### The player disappears behind other windows

Enable:

```text
Settings
→ Position
→ Stay Topmost
```

### The buttons do not respond

Make sure **Click through** is disabled:

```text
Right-click the skin
→ Settings
→ Click through
```

## Credits

- [Rainmeter](https://www.rainmeter.net/)
- [RainmeterMediaPlayer](https://github.com/i2002/RainmeterMediaPlayer)
- [Long Pixel-7](https://font.download/font/long-pixel-7)
- Diagram icons: [Lucide](https://lucide.dev), [Simple Icons](https://simpleicons.org)

## Disclaimer

This is an unofficial fan-made Rainmeter skin inspired by **Persona 3 Reload**.

Persona 3 Reload and related trademarks and intellectual property belong to **ATLUS / SEGA** and their respective owners.

This project is not affiliated with or endorsed by ATLUS or SEGA.

Feedback, bug reports, and suggestions are always welcome. Feel free to open an issue or leave a comment.

If you like the skin, consider leaving a ⭐ on the repository.
