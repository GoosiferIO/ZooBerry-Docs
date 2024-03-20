# Game Manager API

The Game Manager API is a collection of functions that allow you to interact with the game's state and control the generalized state of the game. This includes functions to interact with the zoo's budget, pause and resume the game, and retrieve information about the zoo's guests and animals.

| Command  | Description |
| ------------- | ------------- |
| `AddToZooBudget(float deposit)` | Deposit a discrete amount of cash into your zoo budget. Takes a float as an argument. |
| `GetZooBudget()` | Returns the current budget as a float. |
| `SetZooBudget(float new_budget)` | Set your current budget to a new amount. Takes a float as an argument. |
| `IsZooLoaded()` | Is a zoo currently open? Returns a boolean value. |
| `PauseGame()` | Pause the game. |
| `IsGamePaused()` | Is the game currently paused? Returns a boolean value. |
| `NumAnimals()` | Return the current number of animals in your zoo. Returns an integer. |
| `NumSpecies()` | Return the current number of animal species in your zoo. Returns an integer. |
| `NumGuests()` | Return the current number of guests in your zoo. Returns an integer. |
| `NumTiredGuests()` | Return the current number of tired guests in your zoo. Returns an integer. |
| `NumHungryGuests()` | Return the current number of hungry guests in your zoo. Returns an integer. |
| `NumThirstyGuests()` | Return the current number of thirsty guests in your zoo. Returns an integer. |
| `NumGuestsNeedRestrm()` | Return the current number of guests that need to use the restroom. Returns an integer. |
| `NumGuestsInFilter()` | Return the current number of guests in the guest filter. Returns an integer. |
| `GetZooAdmissionCost()` | Return the current admission cost to your zoo. Note: this is the adult ticket value. The child ticket value is not stored in memory as it is automatically calculated from the adult price divided by 2. Returns a float. |
| `SetZooAdmissionCost(float new_adm)` | Set the current admission cost to your zoo. See the above limitation about child ticket prices. Takes one float as an argument. |
| `AdmissionsIncomeByMonth()` | Retrieve an array containing 12 elements, each representing admissions income for a specific month. |
| `ConcessionsBenefitByMonth()` | Retrieve an array containing 12 elements, each representing the concessions benefit for a specific month. |
| `ZooValueByMonth()` | Retrieve an array containing 12 elements, each representing the zoo value for a specific month. |
| `PrivateDonationsByMonth()` | Retrieve an array containing 12 elements, each representing the private donations for a specific month. |
| `ZooRatingByMonth()` | Retrieve an array containing 12 elements, each representing the zoo rating for a specific month. |
| `ConstructionCostByMonth()` | Retrieve an array containing 12 elements, each representing the construction costs for a specific month. |
| `AnimalPurchaseCostsByMonth()` | Retrieve an array containing 12 elements, each representing the animal adoption costs for a specific month. |
| `_globalAnimalRating` | Global variable. Sets the animal rating per update. |
| `_globalZooRating` | Global variable. Sets the zoo rating per update. |
| `_globalGuestRating` | Global variable. Sets the guest rating per update. |
