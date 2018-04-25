# Godot Oculus GDNative module
This module is provided as is, all files are contained within the addons/godot-oculus folder

The scenes subfolder contains a number of godot scenes that help you set up your project. 
For basic functionality start with adding oculus_first_person.tcn to your project.
Also make sure that vsync is turned off in your project settings.

There is support for touch controllers. Note that Godot already supports the XBox One controller natively so this is not part of the module. Other controller support may be added later.

This module only has support for Windows and the Oculus client software must be installed.
Oculus does not (yet) supply an environment for Mac OS X nor Linux.
This module does not support Gear VR.

Source code for this module can be found here:
https://github.com/BastiaanOlij/godot_oculus

Using the main viewport
-----------------------
The ARVR server module requires a viewport to be configured as the ARVR viewport. If you chose to use the main viewport an aspect ratio corrected copy of the left eye will be rendered to the viewport automatically.

You will need to add the following code to a script on your root node:

```
var interface = ARVRServer.find_interface("Oculus")
if interface and interface.initialize():
	get_viewport().arvr = true
```

Using a separate viewport
-------------------------
If you want control over the output on screen so you can show something independent on the desktop you can add a viewport to your scene and set the arvr property to true and hdr property to false. It is important that the ARVR nodes are child nodes within this viewport. You can add a normal camera to your scene to render a spectator view or turn the main viewport into a 2D viewport and save some rendering overhead.

You can now simplify you initialisation code on your root node to:

```
var interface = ARVRServer.find_interface("Oculus")
if interface:
	interface.initialize()
```

(note that this is still experimental)

Licensing
---------
The Godot Oculus module and the godot scenes in this add on are all supplied under an "unlicense".
The touch controller meshes are copyright Oculus, I'm not sure of the license.

About this repository
---------------------
This repository was created by and is maintained by Bastiaan Olij a.k.a. Mux213

You can follow me on twitter for regular updates here:
https://twitter.com/mux213

Videos about my work with Godot including tutorials on working with VR in Godot can by found on my youtube page:
https://www.youtube.com/channel/UCrbLJYzJjDf2p-vJC011lYw
