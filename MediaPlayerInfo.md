Media Player for ESPhome Display
=

# Overview
The ESPhome display is a device that displays information about the media playing on a specific media player in Home Assistant.  Displayed information includes:
* Track Title
* Artist Name
* Album Artwork (fetched live from Home Assistant via HTTP)
* Playback State (e.g. playing, paused, idle, off)
* If a song's elapsed time and length are available, show a progress bar showing time elapsed for the song and it's total time.  Otherwise, hide the progress.

The header bar shows the device's friendly name and a Wi-Fi/HA connection status icon (shown only when Home Assistant is connected).  Also, show the current time at the rightmost part of the header.

# Hardware
Use the hardware definitions in the following file:
* guiton-template.yaml

# Other Specifications
* The backlight is on at boot (ALWAYS_ON restore mode) and is exposed to Home Assistant as a dimmable light entity so brightness can be adjusted remotely.
* If nothing is playing, the backlight shuts off after 30 seconds.
* Touching the screen while the display is blanked (LVGL paused) wakes the display back up and turns on the backlight if it's off.
* A boot splash screen is shown while the device is connecting. It is dismissed automatically when Home Assistant connects, or can be tapped to dismiss manually.
* Album art is fetched from the HA media player proxy. A download delay is applied after the track changes before downloading, to allow the HA proxy to cache the new image. On error, the previous image is retained.  The download delay is exposed to Home Assistant as a slider that ranges from 0 to 1500 ms.

