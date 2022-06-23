# my key mapping
This is a key mapper setting file for me.
It update udev DB configulation.

# Usage
Auto installing script is available.
It copies hwdb file to /etc/udev/hddb.d and updates udev DB. It overwrites a file, if a file of same name is exist.
```
sudo ./install.bash
```

# Tuning
## First you have to know key codes for remapping
Run and proper event file.
```
sudo evtest
```
Push a key you want to remap and memo key codes and a key names

Also you have to memo the Input device ID.
If you get below
```
Input device ID: bus 0x3 vendor 0x46d product 0x408a version 0x111
```
, then it had to be converted into ```evdev:input:b0003v064Dp408A*```.
Format is 
```
evdev:input:b${bus}v${vendor}p${product}
```
.Where things in ${} are the numbers that are in ```Input device ID: ***```, padded with 0s to be length 4 and capitalized.
```*``` wildcard character can be used.

## write mapping settings
Write above setting fisrt line in hwdb file, and add below key mapping settings.
This means key that have 70039 of key code is converted into tab key.
```
KEYBOARD_KEY_70039=tab
```
Head number in file name means priority to load. Smaller number is High priority.
Following name is anything you want to.
