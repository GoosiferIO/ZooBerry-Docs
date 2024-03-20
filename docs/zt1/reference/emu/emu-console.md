# Command Console

The API includes a command console not originally available in the vanilla game. It can be accessed via `CTRL + J`. Commands will not run unless a zoo is loaded.

Console limitations to consider as of **EMU v1.0.0-alpha.5**:  

- The console is only visible in windowed mode and will not be accessible if you are full screen.  
- Console stays ontop of the main game window (in windowed mode) and will stay ontop of other windows if game is minized. If it's obtrusive, close the console with `exit`. 
- Be careful: Like other shells, `CTRL + C` will exit the console, but it will also close the game.

## Console Commands

| Command  | Description |
| ------------- | ------------- |
| exit  | Safely close the console window. |
| addtobudget <float deposit> | Deposit a discrete amount of cash into your zoo budget. |
| getbudget | Returns the current budget. |
| setbudget <float new_budget> | Set your current budget to a new amount. |
| pause | Pause your game from the console. |
| resume | Resume your game from the console. |