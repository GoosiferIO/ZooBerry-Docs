# Zoo Tycoon 1 File Formats

## File Formats

Blue Fang used a custom `.INI` file implementation to handle the game's entity and system configuration. Making copies of asset directories containing these configuration files allowed for modders to create their own expansive content for the game. The game also has its own set of proprietary graphics formats that require other tools to extract. Below are common file formats relevant to modders interested in making their own content for the game:

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `lang*.dll`         | Dynamically-linked library | Data serialization | Resource Hacker, Risoh Editor |
| `*.cfg`             | Configuration | Game systems configuration | Any text editor* |
| `*.ani`             | Animation | Animation configuration | Any text editor* |
| `*.scn`             | Scenario | Scenario configuration | Any text editor* |
| `*.ucb`             | User-Created Building | Building configuration | Any text editor* |
| `*.ucs`             | User-Created Scenery | Scenery configuration | Any text editor* |
| `*.uca`             | User-Created Animal | Animal configuration | Any text editor* |
| `*.ai`              | Artificial Intelligence | Official entity (AI) configuration | Any text editor* |
| `*.pal`             | Pallette | Color palette                | ZooT, APExp, ZT Studio |
| No extension        | None | Graphics file | ZooT, APExp, ZT Studio  |
| `*.wav`             | Wave Sound File | Sounds | Audacity, Audition, Tenacity |
| `*.zoo`             | Zoo | Zoo Tycoon save | Any text editor* |
| `*.ztd`            | Zoo Tycoon Data | Packaged assets  | 7zip |
| `*.lyt`             | Layout | Layout configuration | Any text editor* |
| `*.bmp`             | Bitmap | Fring and grid graphics | GIMP, any graphics editor |
| `*.lle`             | Unknown | Pre-rendered terrain blending graphics | Unknown |
| `*.tga`             | Targa | Award, terrain, and user interface graphics | GIMP, any graphics editor |
| `*.txt`             | Text | Non-localized text and user-made animal info | Any text editor* |

!!! note "*`lang*.dll`"
    Contains Zoo Tycoon Localizable Resources using TEXT, BITMAP, MENU, DIALOG, STRINGTABLE, and ACCELERATORS blocks.

!!! note "*Text Editors"
    Any text editor that can handle line endings that have 1 or 2 control characters. This includes WordPad that comes with MS Windows, but not Notepad because Notepad understands only 1 type of line ending. VS Code in particular is a fantastic option.

!!! note "`*.ztd` Files"
    `*.ztd` files are just zip files and can be opened with any zip utility. 7zip is a known quantity and easily-accessible, but chances are you probably have a similar utility installed already.

These files can all be found inside of the game's default install directory at `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`.

