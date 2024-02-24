# Mod Installation

Depending on the version of Zoo Tycoon 1 you own, the mod install directory might be different. The type of file you want to install might be important as well. Try these out and see which works for you.

## Important

- **Turn off the game**: Though it shouldn’t cause any issues if we were to install a mod while your game is running, it makes sense to have it shut down so that any changes show up on a re-launch.
- **Unzip your files**: Usually files are in `.zip` format and will require access to a zip utility. Below are resources that can get you started.
    - [Zipping/Unzipping files with the default Windows zip utility](https://support.microsoft.com/en-us/windows/zip-and-unzip-files-f6dde0a7-0fec-8294-e1d3-703ed85e7ebc)
    - Zipping/Unzipping files with 7-Zip
        - [Download 7-Zip](https://www.7-zip.org/download.html)
        - [How to use 7-Zip](https://7ziphelp.com/how-to-use-7-zip)

## Installing Entity Mods

An entity in Zoo Tycoon can be described as any animal or object (buildings, foliage, etc). Installing custom entities in Zoo Tycoon 1 is easy and amounts to a simple drag and drop.

1. First, go to the ZT1 root folder.

    `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon\`

2. If you have a dlupdate folder, drop your .ztd file there:

    `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon\dlupdate`

3. If you do not have a dlupdate folder, drop your .ztd file into the Updates folder instead:

    `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon\Updates`

The install directory changes depending on the version of the game you own but these instructions should be consistent.

## Lang Files

Importantly, Zoo Tycoon mods will often add new UI strings, things like guest thoughts, zoopedia entries, and other additions that require the inclusion of a `.dll` file in your installation process. This `.dll` file serves as a serialized data container with most of the strings in the game. Community nomenclature has dubbed these files ’lang files’ because they are always prefixed by the ’lang’ identifier.

If your mod requires a lang file, simply download the referenced version in the mod instruction blurb, extract the .dll file, and drop it into the root Zoo Tycoon game directory:

`C:\Program Files (x86)\Microsoft Games\Zoo Tycoon\`

Note: Not all ZT1 mods make use of lang files, so it is fine if your file instructions do not mention one.

## Installing Zoos

`.zoo` files are the Zoo Tycoon 1 save file format and is used for both the zoo maps themselves after saving the game and for scenarios.

To install a zoo save file, drop it into the following directory:

`C:\Program Files\Microsoft Games\Zoo Tycoon\Saved Games`

## Installing Scenarios

If you happen to have a copy of one of the few custom scenarios and wish to install it, simply drop the .zoo file in the following directory. Any accompanying .ztd and lang files are installed the same as explained above.

`C:\Program Files\Microsoft Games\Zoo Tycoon\Maps`