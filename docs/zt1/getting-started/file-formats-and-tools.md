# Zoo Tycoon 1 File Formats and Tools to Open Themm

## File Formats

Blue Fang used a custom `.INI` file implementation to handle the game's entity and system configuration. Making copies of asset directories containing these configuration files allowed for modders to create their own expansive content for the game. The game also has its own set of proprietary graphics formats that require other tools to extract. Below are common file formats relevant to modders interested in making their own content for the game:

### Configuration Files

!!! info "*Text Editors"
    Any text editor that can handle line endings that have 1 or 2 control characters. This includes WordPad that comes with MS Windows, but not Notepad because Notepad understands only 1 type of line ending. VS Code in particular is a fantastic option.

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `*.cfg`             | Configuration | Game systems configuration | Any text editor* |
| `*.ani`             | Animation | Animation configuration | Any text editor* |
| `*.scn`             | Scenario | Scenario configuration | Any text editor* |
| `*.ucb`             | User-Created Building | Building configuration | Any text editor* |
| `*.ucs`             | User-Created Scenery | Scenery configuration | Any text editor* |
| `*.uca`             | User-Created Animal | Animal configuration | Any text editor* |
| `*.ai`              | Artificial Intelligence | Official entity (AI) configuration | Any text editor* |
| `*.lyt`             | Layout | Layout configuration | Any text editor* |
| `*.txt`             | Text | Non-localized text and user-made animal info | Any text editor* |

??? "Recommended tools to edit configuration files"

    | Tool | Where to Find | Relevent File Types it Opens | Description | 
    | ---- | ------------- | ------------------- | ----------- |
    | Notepad++ | [Notepad++](https://notepad-plus-plus.org/) | `.txt`, `.ucs`, `.ai`, `.scn`, `.ani`, `.cfg`, `.ucb`, `.uca`, `.pal`, `.lyt`, `.txt` | Notepad++ is a free and open-source text editor. It can be used to edit many of the text-based files found in the game. |
    | VS Code | [Visual Studio Code](https://code.visualstudio.com/) | `.txt`, `.ucs`, `.ai`, `.scn`, `.ani`, `.cfg`, `.ucb`, `.uca`, `.pal`, `.lyt`, `.txt` | Visual Studio Code is a free and open-source text editor. It can be used to edit many of the text-based files found in the game. |


### Asset Packs

!!! info "`*.ztd` Files"
    `*.ztd` files are just zip files and can be opened with any zip utility. 7zip is a known quantity and easily-accessible, but chances are you probably have a similar utility installed already.

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `*.ztd`             | Zoo Tycoon Data | Packaged assets  | 7zip |

??? "Recommended tools to open `*.ztd` files"

    | Tool | Where to Find | Relevent File Types it Opens | Description | 
    | ---- | ------------- | ------------------- | ----------- |
    | 7-Zip | [7-Zip](https://www.7-zip.org/) | `.ztd` | 7-Zip is a free and open-source file archiver. It can be used to extract and compress `*.ztd` files. |

### Graphics Files

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| No extension        | None | Graphics file | ZooT, APExp, ZT Studio  |
| `*.bmp`             | Bitmap | Fring and grid graphics | GIMP, any graphics editor |
| `*.lle`             | Unknown | Pre-rendered terrain blending graphics | Unknown |
| `*.tga`             | Targa | Award, terrain, and user interface graphics | GIMP, any graphics editor |
| `*.pal`             | Pallette | Color palette                | ZooT, APExp, ZT Studio |

??? "Recommended tools to open terrain graphic files"
    | Tool | Where to Find | Relevent File Types it Opens | Description | 
    | ---- | ------------- | ------------------- | ----------- |
    | GIMP | [GIMP](https://www.gimp.org/) | `.bmp`, `.tga` | GIMP is a free and open-source raster graphics editor. It can be used to create and edit `*.bmp` and `*.tga` files found in the game. |

??? "Recommended tools to open the proprietary graphics files"

    !!! info
        The link to Zoot 1.1 goes down on occasion. If you are unable to access the link, you might need to wait a few days for it to come back up due to server issues.

    | Tool | Where to Find | Relevent File Types it Opens | Description | 
    | ---- | ------------- | ------------------- | ----------- |
    | Zoot 1.1 | [Zoot 1.1](http://www.ztcdd.org/DG/index.php?topic=4773.0) | Proprietary graphics files for the game do not have an extension, `*.pal` | Zoot 1.1 is a modding tool that can be used to create and edit ZT1 proprietary graphics files. Note: Zoot 1.1 is found in the second comment. |
    | ZT Studio | [ZT Studio](https://github.com/jbostoen/ZTStudio) | Proprietary graphics files for the game do not have an extension, `*.pal` | ZT Studio is a modding tool that can be used to create and edit ZT1 proprietary graphics files. |

### Misc Binary Files

!!! info "`lang*.dll`"
    Contains Zoo Tycoon Localizable Resources using TEXT, BITMAP, MENU, DIALOG, STRINGTABLE, and ACCELERATORS blocks.

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `lang*.dll`             | Dynamic Link Library | Localizable resources | Resource Hacker, Risoh Editor |
| `*.zoo`             | Zoo | Zoo Tycoon save | Zoo Tycoon 1, Any hex editor |
| `*.wav`             | Wave Sound File | Sounds | Audacity, Audition, Tenacity |

??? "Recommended tools to open `lang*.dll` files"
    | Tool | Where to Find | Relevent File Types it Opens | Description | 
    | ---- | ------------- | ------------------- | ----------- |
    | Resource Hacker | [Resource Hacker](http://www.angusj.com/resourcehacker/) | `lang*.dll` | Resource Hacker is a free and open-source resource editor for Windows applications. It can be used to edit the game string tables. |
    | Risoh Editor | [Risoh Editor](https://github.com/katahiromz/RisohEditor) | `lang*.dll` | Risoh Editor is a free and open-source resource editor for Windows applications. It can be used to edit the game string tables. |

??? "Recommended tools to open `*.wav` files"
    | Tool | Where to Find | Relevent File Types it Opens | Description | 
    | ---- | ------------- | ------------------- | ----------- |
    | Audacity | [Audacity](https://www.audacityteam.org/) | `.wav` | Audacity is a free and open-source digital audio editor and recording application. It can be used to edit and create `.wav` files. |
    | Tenacity | [Tenacity](https://tenacityaudio.org/) | `.wav` | Tenacity is a free and open-source digital audio editor and recording application. It can be used to edit and create `.wav` files. |

These files can all be found inside of the game's default install directory at `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`.
