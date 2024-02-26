# Zoo Tycoon 1 File Formats

## File Formats

Blue Fang used a custom `.INI` file implementation to handle the game's entity and system configuration. Making copies of asset directories containing these configuration files allowed for modders to create their own expansive content for the game. The game also has its own set of proprietary graphics formats that require other tools to extract. Below are common file formats relevant to modders interested in making their own content for the game:

### Configuration Files

!!! note "*Text Editors"
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

### Asset Packs

!!! note "`*.ztd` Files"
    `*.ztd` files are just zip files and can be opened with any zip utility. 7zip is a known quantity and easily-accessible, but chances are you probably have a similar utility installed already.

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `*.ztd`             | Zoo Tycoon Data | Packaged assets  | 7zip |

### Graphics Files

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| No extension        | None | Graphics file | ZooT, APExp, ZT Studio  |
| `*.bmp`             | Bitmap | Fring and grid graphics | GIMP, any graphics editor |
| `*.lle`             | Unknown | Pre-rendered terrain blending graphics | Unknown |
| `*.tga`             | Targa | Award, terrain, and user interface graphics | GIMP, any graphics editor |
| `*.pal`             | Pallette | Color palette                | ZooT, APExp, ZT Studio |

### Misc Binary Files

!!! note "*`lang*.dll`"
    Contains Zoo Tycoon Localizable Resources using TEXT, BITMAP, MENU, DIALOG, STRINGTABLE, and ACCELERATORS blocks.

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `lang*.dll`             | Dynamic Link Library | Localizable resources | Resource Hacker, Risoh Editor |
| `*.zoo`             | Zoo | Zoo Tycoon save | Zoo Tycoon 1, Any hex editor |
| `*.wav`             | Wave Sound File | Sounds | Audacity, Audition, Tenacity |

These files can all be found inside of the game's default install directory at `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`.
