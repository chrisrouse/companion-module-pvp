# Renewed Vision PVP 3

*This module only supports PVP version 3.1 and above.*

Go to [Renewed Vision](https://renewedvision.com/provideoplayer/) to learn more about the software.

> ProVideoPlayer (PVP) is a Mac-based software application designed to play back and manipulate video across one or more screens.

> For over a decade, productions and installations have used ProVideoPlayer for playback to one or more screens along with other tools as part of the full rig: ProPresenter for text and CG, a video rig for camera shots and live produced content, and an expensive screen control system to pull it all together. For many events, a lot of powerful and expensive equipment is radically under-utilized, so we set out to see if we could make a single product that would provide the tools needed for many productions when the complexity of more expensive solutions is unnecessary. That is the vision realized with PVP3.



## Configuration

**Prepare PVP**

First open Preferences in PVP, open the Network tab, and enable network API support.

Choose a port to listen on. Make sure `Use HTTPS Connection` and `Require Authentication` are unchecked, as this module doesn't support those options yet.



**Configure Companion**

Enter in the IP address and port PVP is running on:

- **PVP IP**: The IP address of the PVP instance you want to control.
- **PVP Port**: The port PVP is running on (as shown in PVP's Preferences).



### Backup Instance

If you only have a single PVP instance, leave the following fields empty.

If you have two PVP installations that are running in a primary/backup mode, you may want actions to go to each PVP install to keep them in sync. Instead of creating two PVP instances in Companion and adding the same action for both instances, just add the backup PVP's connection information and let the module handle the work for you:

- **PVP IP (Backup instance)**: The IP address of the backup PVP instance.
- **PVP Port (Backup instance)**: The port the backup PVP instance.

All actions sent to the primary PVP instance will then be mirrored to the backup instance.

If you ever need to send an action to just one of the two PVP installations, you'll need to create a second PVP module instance in Companion and add those actions there.



**Relative Layer Opacities**

If you're using the relative layer opacity action and have a backup instance, please be aware that the opacity is relative to each instance's layer opacity. 



**Network Backup Triggering** 

PVP 3.2 added a network backup triggering mode, which can automatically keep two (or more) PVP instances in sync. This is a great solution if you're controlling PVP from its interface, but not so much if you control the master externally and it fails.

If you use the backup instance feature in this module, be sure to disable PVP's Network Backup Trigger feature.



## Important Notes

Whenever you see `Layer ID` or `Playlist ID` mentioned in an action, you can reference it in one of two ways:

- By its full name (as displayed in PVP). This is the easiest way. A name is case-sensitive.
- By its index. For example, the first layer has an index of `0`, the second has an index of `1`, etc.

Number IDs are always interpreted as indexes, even if a layer or playlist has a numeric name.

**Live Video:** A playlist ID of `-1` refers to the `Live Video` playlist.



## Actions

### Clear/Hide/Mute Layer/Workspace

| Action           | Description                              |
| ---------------- | ---------------------------------------- |
| Clear Layer      | Clears the specified layer of all media. |
| Mute Layer       | Mutes the audio in specified layer.      |
| Unmute Layer     | Unmutes the audio in the layer.          |
| Hide Layer       | Hides the specified layer.               |
| Unhide Layer     | Unhides the layer.                       |
| Clear Workspace  | Clears all the layers in the workspace.  |
| Mute Workspace   | Mutes the audio in the workspace.        |
| Unmute Workspace | Unmutes the audio in the workspace.      |
| Hide Workspace   | Hides the workspace.                     |
| Unhide Workspace | Unhides the workspace.                   |



### Select Layer/Workspace

| Action          | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| Select Layer    | Selects the layer in PVP.  <br />Set `Target Layer`to `Yes` to make the layer the target of untargeted media. |
| Select Playlist | Selects the playlist.                                        |



### Trigger

| Action                           | Description                                        |
| -------------------------------- | -------------------------------------------------- |
| Trigger Cue                      | Triggers a cue by its ID in the selected playlist. |
| Trigger Playlist                 | Triggers the first cue in the playlist.            |
| Trigger Cue in Playlist          | Triggers the cue in the playlist.                  |
| Trigger Cue in Playlist on Layer | Triggers the cue media in the playlist on a layer. |



### Layers/Workspace

| Action                  | Description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| Layer Blend Mode        | Sets the layer's blend mode. The default blend mode is `Normal`. |
| Layer Opacity           | Sets the layer's opacity by percentage; a whole number from `0` to `100`.  <br />You can also make relative opacity adjustments by prefixing the value with a `+` or `-`. |
| Layer Preset            | Applies a preset to the specified layer. Leave the `Preset Name` option empty to unlink the layer's preset. |
| Layer Target Set        | Changes the layer's target set.  <br />A PVP bug prevents target sets from being addressed by index. It can only be addressed by its name. |
| Layer Effect Preset     | Sets the layer's effect preset by its name.  <br />Leave the `Effect Preset Name` field empty to clear all effects. |
| Workspace Effect Preset | Sets the workspace's effect preset by its name.<br />Leave the `Effect Preset Name` field empty to clear all effects. |



## Error Codes

The following table is from the PVP API documentation:

| Error Code | Meaning                                                      |
| ---------- | ------------------------------------------------------------ |
| 400        | Bad Request -- Your request was invalid.                     |
| 401        | Unauthorized -- Authorization failed.                        |
| 403        | Forbidden -- The endpoint requested is hidden for administrators only. |
| 404        | Not Found -- The specified endpoint could not be found.      |
| 405        | Method Not Allowed -- You tried to access an endpoint with an invalid method. |
| 500        | Internal Server Error -- We had a problem with our server. Try again later. |
| 503        | Service Unavailable -- We're temporarily offline for maintenance. Please try again later. |


## Presets

The included Presets can be used to quickly create basic buttons for Layers and Workspace.

| Presets for Layers    | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| Clear Layer #         | Clear a specific layer.                                              |
| Mute Layer #          | Mute a specific layer.                                               |
| Unmute Layer #        | Unmute a specific layer                                              |
| Mute/Unmute Layer #   | Mute and unmute a specific layer with a Key down and Key up action.  |
| Select Layer #        | Select a specific layer.                                             |
| Hide/Show Layer #     | Hide and unhide a specific layer with a Key down an Key up action.   |
| Select Playlist       | Select a specific playlist.                                          |
| Trigger Cue           | Trigger a cue in the current playlist.                               |

| Presets for Workspace | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| Clear Workspace       | Clears the workspace (all layers).                                   |
| Mute Workspace        | Mute the workspace.                                                  |
| Unmute Workspace      | Unmute the workspace.                                                |
| Mute/Unmute Workspace | Mute and unmute the workspace with a Key down and Key up action.     |

------

For additional actions, please raise a feature request on [GitHub](https://github.com/bitfocus/companion-module-pvp/).