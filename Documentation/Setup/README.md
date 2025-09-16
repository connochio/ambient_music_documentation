# Installation

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=connochio&repository=ambient_music&category=Integration)

You can install this integration via HACS with the link above.  

Alternatively, you can install this integration by manually adding it to the custom_components folder using the commands below via SSH:  
```
cd config   # where configuration.yaml lives
mkdir custom_components # if this does not already exist
cd custom_components
git clone https://github.com/connochio/ambient_music.git
ha core restart
```
<br />

# Setup

Ambient Music requires some components to be set up manually via the config flow (cog icon) within the integration to function.

These components are:  
- [Playlists](https://github.com/connochio/ambient_music_documentation/tree/main/Documentation/Setup#add-playlist) - Required
- [Blockers](https://github.com/connochio/ambient_music_documentation/tree/main/Documentation/Setup#manage-blockers) - Optional
- [Media Players](https://github.com/connochio/ambient_music_documentation/tree/main/Documentation/Setup#media-players) - Required

To start using the Ambient Music system, at least one playlist and at least one media player is required to be set up.  
Some automations to call the Ambient Music services are also required, and the system will be automatic from then on.

Blueprints for some starter automations can be found in [the blueprints documentation](https://github.com/connochio/ambient_music_documentation/tree/main/Documentation/Blueprints).

Optionally, blockers can be configured that can more finely control when Ambient Music is active or not.
<br />
<br />

# Configuration

After installation of the integration via HACS, the Ambient Music integration will be available within the integrations page within the Home Assistant settings.

After adding the integration, some sensors/entities will be automatically created without any setup.  
For more information on these sensors/entities, see [the sensors documentation](https://github.com/connochio/ambient_music_documentation/tree/main/Documentation/Sensors).  

Further configuration is required to enable the Ambient Music system however.  

Clicking on the gear icon within the Ambient Music integration will give you some options:
<br />
<br />
## Add Playlist

After clicking on this, you will be asked to provide a playlist name and spotify ID.  
<br />
### Name
This name will be used throughout the integration, and may include special characters.  

It cannot be changed after it has been created however.  
<br />
### Spotify ID

> [!TIP]
> This box will accept both a full spotify URL or 22-char ID

The Spotify ID can obtained from the [Spotify website](https://spotify.com), and this box will accept either a raw 22-character ID or a full URL for ease-of-use.  

An example for this would be:  
`https://open.spotify.com/playlist/0vvXsWCC9xrXsKd4FyS8kM`

The ID for this playlist would be:  
`0vvXsWCC9xrXsKd4FyS8kM`
<br />
<br />

## Manage Blockers

This option will allow you to set up, edit or remove "blockers" from the Ambient Music system.  

Blockers are either entity states or user-created templates that block Ambient Music from running.
<br />
<br />

### Add Blocker

This option will allow you to add a blocker via 2 methods, selectable via radial buttons.

If the state option is selected, you will be prompted to give the blocker a name, select an entity, and a desired state for that entity.  
If the template option is selected, you will be prompted to give the blocker a name, and enter a template.  

> [!TIP]
> The state option is great for single entities.
> 
> The template options is great for more advanced checks.

When the entity is in the desired state, the blocker will return as `true` and block the usage of Ambient Music.  

You may also opt to invert the outout of the state or template.  
If the state or template return a `true` result, and the invert option is selected, `false` will be given for the purposes of Ambient Music, and vice versa.  

<details><summary>Example inverted blocker</summary>
<br />
A good example of where this may be useful is if you would like to limit Ambient Music to only work when someone is at home.  

An example entity and state for this would be:  
Entity: `person.connochio`  
State: `home`  
Invert: `True`  

In this configuration, if the location of person.connochio is anything <i>other</i> than `home`, Ambient Music will be blocked from running.
</details>
<br />

### Edit Blocker

> [!NOTE]
> This option will only appear after the first blocker has been created.

This option will allow you to edit the name, entity/state for a state-based blocker, or the template for a template-based blocker.  
<br />

### Remove Blockers

> [!NOTE]
> This option will only appear after the first blocker has been created.

This option will allow blockers to be removed via bulk selection via checkboxes.  
Removed playlists will also have any binary sensors related to them removed.
<br />
<br />

## Manage Playlists

> [!NOTE]
> This option will only appear after the first playlist has been created.

This option will allow you to edit and remove playlists from the Ambient Music system.

Select an action and a playlist from the dropdown menu to continue with that action after clicking Submit.

> [!IMPORTANT]
> Renaming playlists is not supported currently.
> If renaming a playlist is needed, it should be removed and recreated.
<br />

## Media Players

This option allows the selection of either a single or multiple media players.  
These media players will be used across the Ambient Music system for playing the playlists.  

The selection supports all media players that are exposed to Home Assistant, but not all of them have been tested and confirmed to be working.  

For best results, use player groups via the Music Assistant add-on to synchronise queues and sync playback.

> [!WARNING]
> Selecting different brands of media players may result in unexpected bahaviour, such as:
> - Music playing out of sync across players.
> - Different tracks playing on separate speakers due to having separate shuffled queues










