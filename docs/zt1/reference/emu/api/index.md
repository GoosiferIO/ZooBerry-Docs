# Scripting API

## Installing EMU Scripts

Create a new folder called `scripts` inside of your main Zoo Tycoon directory: `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`. Drop scripts inside of the scripts folder.

Scripting details:

- EMU supports Lua 5.4.
- Lua scripts must have the `.emu` extension.  
- All scripts will run on the main game loop. Be conservative with loops unless they are predictable and efficient. Global variables might not be effective as they are not guaranteed to persist between script runs.
- All executing code must live inside of an `emu_run` function.  

## Writing Lua Scripts

Files must carry the `.emu` extension and placed in the `/scripts` folder inside of the root Zoo Tycoon 1 folder. All Lua code must be inside of an `emu_run` function to be executed. Any code inside of the `emu_run` function will be executed on the main EMU loop.

Please check out the [Advanced Modding Tutorials](/zt1/advanced/) section for guided tutorials on how to write Lua scripts for Zoo Tycoon 1.

## Supported API Calls

EMU adds scripting support to Zoo Tycoon 1. The following sections detail the available API calls you can use in your Lua scripts.

[Game Manager API](./gamemanager.md)  
[Entity Types API](./entitytypes.md)  
[EMU Console API](./emuconsole-api.md)  
[World Manager API](./worldmanager.md)  
[UI General API](./uigeneral.md)  


