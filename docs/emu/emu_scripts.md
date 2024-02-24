# Lua Scripting

Lua scripting was introduced in **EMU v1.0.0-alpha.3**.

## Supported API Calls

EMU adds scripting support to Zoo Tycoon 1. Currently scripting is limited to the following API calls:

| Command  | Description |
| ------------- | ------------- |
| AddToZooBudget(float deposit) | Deposit a discrete amount of cash into your zoo budget. Takes a float as an argument. |
| GetZooBudget() | Returns the current budget as a float. |
| SetZooBudget(float new_budget) | Set your current budget to a new amount. Takes a float as an argument. |
| IsZooLoaded() | Is a zoo currently open? Returns a boolean value. |
| PauseGame() | Pause the game. |
| IsGamePaused() | Is the game currently paused? Returns a boolean value. |
| NumAnimals() | Return the current number of animals in your zoo. Returns an integer. |
| NumSpecies() | Return the current number of animal species in your zoo. Returns an integer. |
| NumGuests() | Return the current number of guests in your zoo. Returns an integer. |
| NumTiredGuests() | Return the current number of tired guests in your zoo. Returns an integer. |
| NumHungryGuests() | Return the current number of hungry guests in your zoo. Returns an integer. |
| NumThirstyGuests() | Return the current number of thirsty guests in your zoo. Returns an integer. |
| NumGuestsNeedRestrm() | Return the current number of guests that need to use the restroom. Returns an integer. |
| NumGuestsInFilter() | Return the current number of guests in the guest filter. Returns an integer. |
| GetZooAdmissionCost() | Return the current admission cost to your zoo. Note: this is the adult ticket value. The child ticket value is not stored in memory as it is automatically calculated from the adult price divided by 2. Returns a float. |
| SetZooAdmissionCost(float new_adm) | Set the current admission cost to your zoo. See the above limitation about child ticket prices. Takes one float as an argument. |
| AdmissionsIncomeByMonth() | Retrieve an array containing 12 elements, each representing admissions income for a specific month. |
| ConcessionsBenefitByMonth() | Retrieve an array containing 12 elements, each representing the concessions benefit for a specific month. |
| ZooValueByMonth() | Retrieve an array containing 12 elements, each representing the zoo value for a specific month. |
| PrivateDonationsByMonth() | Retrieve an array containing 12 elements, each representing the private donations for a specific month. |
| ZooRatingByMonth() | Retrieve an array containing 12 elements, each representing the zoo rating for a specific month. |
| ConstructionCostByMonth() | Retrieve an array containing 12 elements, each representing the construction costs for a specific month. |
| AnimalPurchaseCostsByMonth() | Retrieve an array containing 12 elements, each representing the animal adoption costs for a specific month. |
| _globalAnimalRating | Global variable. Sets the animal rating per update. |
| _globalZooRating | Global variable. Sets the zoo rating per update. |
| _globalGuestRating | Global variable. Sets the guest rating per update. |

## How to Install EMU Scripts

Create a new folder called `scripts` inside of your main Zoo Tycoon directory: `C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`. Drop scripts inside of the scripts folder.

Scripting info:

- All Lua standard libraries as of Lua 5.3 are made available for your use.  
- Lua scripts must have the `.emu` extension.  
- As of the latest **EMU v1.0.0-alpha.4**, EMU can load any lua scripts inside of a `/scripts` folder inside of the root Zoo Tycoon 1 folder.  
- Lua support is designed for modders to take control of the game logic by having individual scripts run on the main EMU loop. If/then statements are obviously encouraged, but be conservative with your own loops unless they are predictable and efficient. Global variables might not be effective.  
- All executing code must live inside of an `emu_run` function.  

**Example Lua Script:**
_playground.emu_
```Lua
function emu_run()
    -- pause the game if the budget goes above $400,000
    if GetZooBudget() > 400000 and IsGamePaused() == false then
        io.write("Pausing the game")
        PauseGame(true)
    -- resume game if budget dips below $400,000 (maybe the console can save us here?)
    elseif GetZooBudget() <= 400000 and IsGamePaused() == true then
        io.write("Resuming the game")
        PauseGame(false)
    end
end
```