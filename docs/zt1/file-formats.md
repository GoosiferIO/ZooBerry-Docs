# Zoo Tycoon 1 File Formats

## File Formats

Blue Fang used a custom `.INI` file implementation to handle the game's entity and system configuration. Making copies of asset directories containing these configuration files allowed for modders to create their own expansive content for the game. The game also has its own set of proprietary graphics formats that require other tools to extract. Below are common file formats relevant to modders interested in making their own content for the game:

| File Extension | Implied Monikor | Purpose | Suggested Tools to Open |
| -------------- | --------------- | ------- | ------------- |
| `lang*.dll`         | Dynamically-linked library | Data serialization | Any hexadecimal editor |
| `*.cfg`             | Configuration | Game systems configuration | Any text editor |
| `*.ani`             | Animation | Animation configuration | Any text editor |
| `*.scn`             | Scenario | Scenario configuration | Any text editor |
| `*.ucb`             | User-Created Building | Scenery configuration | Any text editor |
| `*.uca`             | User-Created Animal | Animal configuration | Any text editor |
| `*.ai`              | Unknown | Official entity configuration | Any text editor |
| `*.pal`             | Pallette | Color palette                | ZooT, APExp, ZT Studio |
| No extension        | None | Graphics file | ZooT, APExp, ZT Studio  |
| `*.wav`             | Wave Sound File | Sounds | Audacity, Audition, Tenacity |

These files can all be found inside of the game's default install directory at `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`.