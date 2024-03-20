# Game Manager API

## Overview

The Game Manager API is a collection of functions that allow you to interact with the game's state and control the generalized state of the game. This includes functions to interact with the zoo's budget, pause and resume the game, and retrieve information about the zoo's guests and animals.

## Usage

## Definitions

| Command  | Description |
| ------------- | ------------- |
| `addCash(float deposit)` | Deposit a discrete amount of cash into your zoo budget. |
| `setCash(float new_budget)` | Set your current budget to a new amount. |
| `pauseGame()` | Pause the game. |
| `isGamePaused()` | Is the game currently paused? Returns a boolean value. |
| `freezeGameState()` | Freeze the game state. |
| `isZooLoaded()` | Is a zoo currently open? Returns a boolean value. |
| `numAnimals()` | Return the current number of animals in your zoo. Returns an integer. |
| `numSpecies()` | Return the current number of animal species in your zoo. Returns an integer. |
| `numGuests()` | Return the current number of guests in your zoo. Returns an integer. |
| `admissionsIncomeByMonth()` | Retrieve an array containing 12 elements, each representing admissions income for a specific month. |
| `concessionsBenefitByMonth()` | Retrieve an array containing 12 elements, each representing the concessions benefit for a specific month. |
| `zooProfitOverTime()` | Retrieve an array containing 12 elements, each representing the zoo profit for a specific month. |
| `privateDonationsByMonth()` | Retrieve an array containing 12 elements, each representing the private donations for a specific month. |
| `zooRatingByMonth()` | Retrieve an array containing 12 elements, each representing the zoo rating for a specific month. |
| `constructionCostByMonth()` | Retrieve an array containing 12 elements, each representing the construction costs for a specific month. |
| `animalPurchaseCostsByMonth()` | Retrieve an array containing 12 elements, each representing the animal adoption costs for a specific month. |
| `researchCostsByMonth()` | Retrieve an array containing 12 elements, each representing the research costs for a specific month. |
| `zooValueByMonth()` | Retrieve an array containing 12 elements, each representing the zoo value for a specific month. |
| `enableDevMode()` | Enable developer mode. |
| `isDevModeEnabled()` | Is developer mode enabled? Returns a boolean value. |
