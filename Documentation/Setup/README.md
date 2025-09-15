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

# Configuration

After installation of the integration via HACS, the Ambient Music integration will be available within the integrations page within the Home Assistant settings.

After adding the integration, some sensors/entities will be automatically created without any setup.  
For more information on these sensors/entities, see [the sensors documentation](https://github.com/connochio/ambient_music_documentation/tree/main/Documentation/Sensors).  

Further configuration is required to enable the Ambient Music system however.  

Clicking on the gear icon within the Ambient Music integration will give you some options:  
<br />

## Add Playlist

After clicking on this, you will be asked to provide a playlist name and spotify ID.  

### Name
This name will be used throughout the integration, and may include special characters.



### Spotify ID

> [!NOTE]
> This box will accept both a full spotify URL or 22-char ID

The Spotify ID can obtained from the [Spotify website](https://spotify.com), and this box will accept either a raw 22-character ID or a full URL for ease-of-use.  

An example for this would be:  
`https://open.spotify.com/playlist/0vvXsWCC9xrXsKd4FyS8kM`

The ID for this playlist would be:  
`0vvXsWCC9xrXsKd4FyS8kM`

## Manage Blockers

This option will allow you to set up, edit or remove "blockers" from the Ambient Music system.  

These blockers are entities or user-created templates that should return a true/false value.  
If any blocker returns true, Ambient Music will either stop playing and be blocked from starting to play a playlist.

Within this option, there are multiple further options:

### Add Blocker

This option will allow you to add a blocker via 2 methods, selectable via radial buttons.

If the state option is selected, you will be prompted to select an entity, and a desired state.  
When the entity is in the desired state, the blocker will return as `true` and block the usage of Ambient Music.  

You may also opt to invert this entity state as well.  
If the entity and state selected return true, and the invert option is selected, the result will be `false` for the purposes of Ambient Music

<details><summary>Example inverted state</summary>
<br />
A good example of where this may be useful is if you would like to limit Ambient Music to only work when someone is at home.  
  
An example entity and state for this would be:  
Entity: `person.connochio`  
State: `Home`  
Invert: `True`  

In this configuration, if the location of person.connochio is <i>not</i> `Home`, then Ambient Music will be blocked from running.
</details>











