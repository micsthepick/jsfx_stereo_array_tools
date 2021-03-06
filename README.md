# Microphone array processing tools

## what is JSFX?

A brief introduction to JSFX: https://www.cockos.com/jsfx/

## How to install a JSFX 

### reaper installation (requires reaper daw)
install/open reaper, go to "Options" -> "Show Reaper Resource path". From here you can move the JSFX plugins into Effects

### reajs installation (windows/wine + any vst2 capable host)
reajs comes with the reaplugs bundle: https://www.reaper.fm/reaplugs/
Run the installer, and then copy the effects to %programfiles%/VstPlugins/ReaPlugs/JS/Effects
(you might need to use %programfiles%/Steinberg/VstPlugins/ReaPlugs/JS/Effects or whatever respective directory the installer uses)

### manual reajs installation
ReaJs_info.txt in the same directory as reajs.dll contains instructions on how to point reajs to a different directory if desired.
If/when you've done so, then just install the effects to your configured location. (this could also be used to point reajs to the same directory that reaper uses, if you like to use jsfx with reaper and other hosts too!)

For developers: https://www.reaper.fm/sdk/js/js.php

## oversampling with subtractive enhancer
This plugin has dependencies - For oversampling to work correctly, you need to copy st-oversampler.jsfx-inc from https://stash.reaper.fm/v/26656/wuff.zip

## subtractive enhancer tutorial
This plugin takes a stereo source (presumably from a stereo omni microphone array) and artificially widens it by subtracting a delayed version of both channels from each other.

In order to have the greatest seperation, you need to approximate the distance between both MEMS microphones, and then enter that distance into the first slider as mm.

You can also control the degree of the effect by Setting Delay Level (db). The default level of -6dB will add ~ 0.5 times the original signal to the other channel, with the appropriate delay. -6dB will probably be fine for most cases.

Finally, oversampling is provided for precise delays, each increment in oversampling will approx. double the processing power used, but gives 2x the precision for the delay

## beamforming tutorial
I've found that combining the subtractive enhancer with the beamformer tends to give superior results than just the beamformer itself. Just make sure to put the subtractive enhancer first in the plugin chain

### credits
Thanks go to Neil Bickford for helping out with other plugins, and for the denoising algorithm used in the beamformer...  
and Sault and Tale for the oversampling algorithm used in the stereo widener.