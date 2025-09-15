# Ambient Music Automation Blueprints
  
Within this section of the documentation are pre-built and ready-to-go blueprints for the base automations that will allow the ambient music system to function.  
  
## Stop Playing

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fconnochio%2Fambient_music_documentation%2Fblob%2Fmain%2FDocumentation%2FBlueprints%2FYaml%2Fstop_playing.yaml)  

This blueprint will call the service that stops ambient music from playing.  

- Triggers:  
  - 'binary_sensor.ambient_music_blockers_clear' changes to an 'Off' state  
- Actions:
  - call service 'ambient_music.stop_playing'
  
When the global blocker sensor turns to an 'Off' state, the service will be called and music will fade down to volume 0 on the confgured media players.  
This will happen over the course of the configured 'volume fade down' within the Ambient Music integration.  
Music will then be paused on the configured media players.  

## Fade Down to Switch Playlist

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fconnochio%2Fambient_music_documentation%2Fblob%2Fmain%2FDocumentation%2FBlueprints%2FYaml%2Fswitch_playlist.yaml)  

This blueprint will call the service that stops ambient music from playing before switching to the new selection.  
  
- Triggers:  
  - 'select.ambient_music_playlists' changes from any state to any state 
- Conditions:
  - 'binary_sensor.ambient_music_blockers_clear' is in an 'On' state
- Actions:
  - call service 'ambient_music.pause_for_switchover'
  
When the playlist selection is switched from any item to any other item, the service will be called and music will fade down to volume 0 on the configured media players.  
This will happen over the course of the configured 'volume fade down' within the Ambient Music integration.  
Music will then be paused on the configured media players.  

## Start Playing Selected Playlist

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fconnochio%2Fambient_music_documentation%2Fblob%2Fmain%2FDocumentation%2FBlueprints%2FYaml%2Fstart_playing.yaml)  

This blueprint will call the service that starts playing the currently selected playlist via the confogured media players.  
  
- Triggers:  
  - 'select.ambient_music_playlists' changes from any state to any state for 'number.ambient_music_volume_fade_down_seconds' + 1 seconds
  - 'binary_sensor.ambient_music_blockers_clear' changes to an 'On' state
- Conditions:
  - 'binary_sensor.ambient_music_blockers_clear' is in an 'On' state
- Actions:
  - call service 'ambient_music.play_current_playlist'
  
When the playlist selection is switched for the music fade down duration + 1 second, or when the global blocker sensor changes to an 'On' state, the service will be called to start playing the selected playlist.  
It will turn the configured media players to volume 0, start playing, and fade the volume up to the configured 'default volume' with the Ambient Music integration. 
