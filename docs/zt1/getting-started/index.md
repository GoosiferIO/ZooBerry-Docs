# Getting Started

!!! warning
    This page is a work in progress and is not yet complete.

Most assets that came packaged with the game are compressed into `*.ztd`, which are actually `*.zip` files so they are quite accessible to extract.  When the game loads it looks for these files, loads them into memory, and sorts them into appropriate entities depending on where in the pre-defined structure (and configuration) the packaged files are stored.

If we were to extract all of the asset and configuration files onto a single folder on the desktop, the structure would look something like this:

!!! note 
    The following is an not yet complete and not an accurate representation of the text above, but is a good starting point for understanding the structure of the game's assets.

```
./building_name
|--- freeform/
|   |---unlocksbuilding.scn
|--- objects/
|   |---<project_codename>
|   |   |---IDLE
|   |   |   |---idle.ani
|   |   |   |---NE
|   |   |   |---NE.pal
|   |   |   |---NW
|   |   |   |---NW.pal
|   |   |   |---SE
|   |   |   |---SE.pal
|   |   |   |---SW
|   |   |   |---SW.pal
|   |   |---NE
|   |   |   |---N
|   |   |   |---N.pal
|   |   |   |---NE
|   |   |---NW
|   |   |   |---N
|   |   |   |---N.pal
|   |   |   |---NW
|   |   |---SE
|   |   |   |---N
|   |   |   |---N.pal
|   |   |   |---SE
|   |   |---SW
|   |   |   |---N
|   |   |   |---N.pal
|   |   |   |---SW
|   |   |---USED
|   |   |   |---idle.ani
|   |   |   |---NE
|   |   |   |---NE.pal
|   |   |   |---NW
|   |   |   |---NW.pal
|   |   |   |---SE
|   |   |   |---SE.pal
|   |   |   |---SW
|   |   |   |---SW.pal
|--- scenery/
|   |---other/
|___|___|---<project_codename>.ucb
```