# Command Console

The API includes a command console not originally available in the vanilla game. It can be accessed via `CTRL + J`. Commands will not run unless a zoo is loaded.

Console limitations to consider as of **EMU v1.0.0-alpha.5**:  

- The console is only visible in windowed mode and will not be accessible if you are full screen.  
- Safety checks are not yet implemented so be careful to stray too far from the expected input.  
- Console stays ontop of the main game window (in windowed mode) and will stay ontop of other windows if game is minized. If it's obtrusive, close the console with `exit`.  
- This API makes use of multi-threading to run EMU and the console simultaneously with the game. On slower hardware you might see propagation of resources take longer between what you see in the game and what you see in a function return value. For example: `num-tiredguests` might say 10, but the game says 11 for a few milliseconds longer. 
- `list-privatedonations` has different values than what the game displays. The array is accurate down to the second that the month changes, but then the game adds an unknown value to the final recorded value on-screen. It is not known if this is a bug or if it is adding other donations like benefactor contributions. We keep it for analysis in the future.  

## Console Commands

| Command  | Description |
| ------------- | ------------- |
| exit  | Safely close the console window. |
| addtobudget <float deposit> | Deposit a discrete amount of cash into your zoo budget. |
| getbudget | Returns the current budget. |
| setbudget <float new_budget> | Set your current budget to a new amount. |
| pause | Pause your game from the console. |
| resume | Resume your game from the console. |
| num-animals | Return the current number of animals in your zoo. |
| num-species | Return the current number of animal species in your zoo. |
| num-guests | Return the current number of guests in your zoo. |
| num-tiredguests | Return the current number of tired guests in your zoo. |
| num-hungryguests | Return the current number of hungry guests in your zoo. |
| num-thirstyguests | Return the current number of thirsty guests in your zoo. |
| num-rstrmguests | Return the current number of guests that need to use the restroom. |
| getzooadmcost | Return the current admission cost to your zoo. Note: this is the adult ticket value. The child ticket value is not stored in memory as it is automatically calculated from the adult price divided by 2. |
| setzooadmcost <float new_adm> | Set the current admission cost to your zoo. See the above limitation about child ticket prices. |
| list-admissionsincome | Return a calendar listing of admissions income. |
| list-concessionsbenefit | Return a calendar listing of concessions benefits. |
| list-zoovalue | Return a calendar listing of zoo value changes over the year. |
| list-privatedonations | Return a calendar listing of private donations. |
| list-zoorating | Return a calendar listing of zoo ratings. |
| list-constructioncosts | Return a calendar listing with construction costs. |
| list-animalpurchasecosts | Return a calendar listing of animal adoption costs. |
| devmode <boolean enable> | Set to true to enable dev mode or false to disable. | 