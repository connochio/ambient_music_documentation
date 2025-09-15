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
State: `Home`  
Invert: `True`  

In this configuration, if the location of person.connochio is anything <i>other</i> than `Home`, Ambient Music will be blocked from running.
</details>











