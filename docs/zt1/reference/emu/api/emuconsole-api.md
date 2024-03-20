# EMU Console API

All commands in this API are static functions and the EMU Console object is available as a global variable in the Lua scripting environment.

Example usage:
```lua
function emu_run()
    EMUConsole.WriteToConsole("Hello, world!") -- writes "Hello, world!" to the console
end
```

| Command  | Description |
| ------------- | ------------- |
| `WriteToConsole(string message)`  | Writes a message to the EMU Console. |