<h1 align="center">EMU | Extensible Modding Utility</h1>

<h3 align="center"> A Zoo Tycoon 1 Scripting API for Modders</h3>

Vanilla Zoo Tycoon 1 has over a 20 year history of modding but users have only been able to modify the game through editing of INI configuration files. This project enhances modding capabilities by giving modders Lua scripting support so that they can create more complex and interesting mods.

### Download

[Download the latest release on Github](https://github.com/openztcc/EMU/releases/latest)

### Compatibility

To use this API, you must:

- Own the Zoo Tycoon Complete Collection, or the base game with both expansions installed.
- Have a Windows 7 or newer operating system.
- Install the [Microsoft Visual C++ 2017 Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170).

### Build from Source

The .sln file has been included for the option to build from source. The project is build with Visual Studio 2022.

### Installation

Drop the res-EMU.dll binary directly into your `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon` game directory.

### References

[Console Documentation](./emu-console.md)  
[Scripting API Documentation](./api/index.md)

### Potential Issues

Due to the nature of how the API runs by injecting code into the running game process and dynamic script execution, your anti-virus software may flag the API as a false positive due to this behavior. This is common with modding tools and is generally safe to ignore.

This API is and will always be open source. If you have any concerns about the safety of the API, you are welcome to inspect the source code yourself or build the API from source.

https://github.com/openztcc/EMU/

It's possible you might need to add the `res-EMU.dll` to your anti-virus software's exclusion list to prevent it from being flagged as a false positive.