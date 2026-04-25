# Credits
This is a fork of [Shringe/dunst-media-control](https://github.com/Shringe/dunst-media-control)

# Android TV/Chromecast Style Volume Notifications using Dunst

This is a Bash script that uses Dunst to show an indicator on the screen when the volume, brightness, and song are changed. It ties into `playerctl` to fetch the current song title/artist/album. It can fetch the album art from a file or URL, and it will cache album art files in `/tmp` to reduce data usage and improve speeds. Album art has been tested with YouTube and Spotify on Arch Linux.

## Dependancies

* PulseAudio/Pipewire-Pulse
* Font Awesome (`apt-get install fonts-font-awesome / `pacman -S ttf-font-awesome`)
* dunst (`apt-get install dunst` / `pacman -S dunst`)
* libnotify (`apt-get install libnotify-bin` / `pacman -S libnotify`)

## Installation

1. Verify that all of the dependencies are installed
2. Edit `media-control` and set your desired values for the configuration options at the top
3. Copy `media-control` to a directory on your PATH
4. Edit `~/.config/dunst/dunstrc`
5. Under the `[global]` section, add `FontAwesome`
6. Change `origin` to `bottom-center` or your desired location

For i3 keybindings:
1. Edit `~/.config/i3/config`
2. Add the following lines:
    ```
    bindsym XF86AudioRaiseVolume exec --no-startup-id media-control volume_up
    bindsym XF86AudioLowerVolume exec --no-startup-id media-control volume_down
    bindsym XF86AudioMute exec --no-startup-id media-control volume_mute
    ```

For labwc keybindings:
1. Edit `~/.config/labwc/labwc/rc.xml`
2. Add the following lines:
    ```
    <keyboard>
        <keybind key="XF86Audio[LowerVolume|RaiseVolume|Mute]">
            <action name="Execute" command="/path/to/volume down|up|mute">
        </keybind>
    </keybaord>
    ```

## Configuration Reference

- `volume_step` - The amount by which the volume should be incremented/decremented each time the script is run
- `max_volume` - The maximum allowable volume. Typically 100.
- `notification_timeout` - The amount of time a notification should stay on the screen, in milliseconds
