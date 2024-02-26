!!! note "Incomplete"
    This page is incomplete. Pull requests welcome.

# Scenario Files `.scn`

Blue Fang provided official documentation for `.scn` files.  The documentation can be found at:

`~/Zoo Tycoon/XPACK2/<unzip scenari6.ztd>/scenario/example.scn`  

## `[desc]`

| Key                  | Value | Description|
|----------------------|------|-----|
| `name` | `<int>` | Takes in the scenario ID property for the scenario name. |
| `story` | `<string name>` | Name of story start |
| `picture` | `<string dir>` | Directory to pictures relevant to story |
| `winstory` | `<string name>` | Name of story win |  
| `winpicture` | `<string dir>` | Directory to pictures relevant to win condition |  
| `losestory` | `<string name>` | Name of story lose |
| `losepicture` | `<string dir>` | Directory to pictures relevant to lose condition |
| `lockedstory` | `<string name>` | Story locked |
| `lockedpicture` | `<string dir>` | Directory to pictures relevant to locked condition |
| `expansion` | `<int>` | Set the default expansion pack `(0 = all, 1 = zoo, 2 = dino, 3 = aqua)` |
| `expansionLocked` | `<int>` | Set this to `0` to allow the user to use the expansion filter, set it to `1` to lock the scenario to the default expansion. |
| `iconf` | `<string dir>` | Failed icon |
| `iconc` | `<string dir>` | Completed icon | 
| `iconp` | `<string dir>` | In progress icon |  

<h3>Example</h3>

From `example.scn` in the game files.

```INI
[desc]
name = 16001
story = SCENARIO_EXAMPLE_START
picture = scenario/scn01/scn01/scn01
winstory = SCENARIO_EXAMPLE_WIN
winpicture = ui/scenario/win/win
losestory = SCENARIO_EXAMPLE_LOSE
losepicture = ui/scenario/lose/lose
lockedstory = SCENARIO_LOCK_STORY_1
lockedpicture = ui/scenario/lock/lock
expansion = 0
iconf = ui/scenario/iconf/iconf
iconc = ui/scenario/iconc/iconc
iconp = ui/scenario/iconp/iconp
```

## `[start]`  

| Key                  | Value | Description|
|----------------------|------|-----|
| `savegame` | `<string dir>` | Filename of the save to load when the scenario starts. |
| `extragoals` | `<string dir>` | List of config files with extra goals to load. |
| `research` | `<research.cfg>` | Research config for the scenario. |
| `marketing` | `mktg.cfg` | Marketing config for the scenario. |
| `setcash` | `<int>` | Amount of cash to start the scenario at, replaces the value in the save. |
| `addcash` | `<int>` | Amount of cash to add to the current amount. |
| `reset` | `<0/1>` | Resets by killing off guests and setting counts to `0`. Same as having all of resetdate, resetanimals, resetguests, resethabitats being set to `1`. |
| `resetdate` | `<0/1>` | Reset the date, finance info, and guests. |
| `resetanimals` | `<0/1>` | Reset the animal numbering |
| `resetguests` | `<0/1>` | Kill off all guests and reset the guest count |
| `resethabitats` | `<0/1>` | Reset the habitat numbering. |  
| `resetfences` | `<0/1>` | Reset the fence strengths. |
| `triggers` | `trigger0` | List of triggers to fire off on scenario start |

<h3>Example</h3>

```INI
[start]
savegame = maps/scn01.zoo
extragoals = scenario/example/extra.scn
research = research.cfg
marketing = mktg.cfg
setcash = 1000000
addcash = 200
reset = 0
resetdate = 1
resetanimals = 1
resetguests = 1
resethabitats = 1
resetfences = 0
triggers = trigger0
```

## `[resume]`  

| Key                  | Value | Description|
|----------------------|------|-----|
| `triggers` | `trigger0` | List of triggers to fire off when scenario resumes |

<h3>Example</h3>

```INI
[resume]
triggers = trigger0
```

## `[completion]`  

On successful completion of the scenario unlock these entities. Can be a list of entities to unlock. For a full list of entity values, please see [Entity IDs](../string-tables/entity-ids.md).

| Key                  | Value | Description|
|----------------------|------|-----|
| `unlock` | `<int>` | Value of entity |

<h3>Example</h3>

```INI
[completion]
unlock = 5000 
unlock = 5001
```

## `[trigger0]`  

Makes all animals unavailable.

<h3>Example</h3>

```INI
[trigger0]
trulea = 4 
truleb = 7
```

## `[duration]`

| Key                  | Value | Description|
|----------------------|------|-----|
| `nummonths` | `<int>` | Number of months that the scenario last for. |
| `display` | `<int>` | No info |
| `text` | `<int>` | Key value of string to display | 
| `icon` | `<string dir>` | Directory to clock icon |

<h3>Example</h3>

```INI
nummonths = 1
display = 1
text = 18000
icon = ui/scenario/clock/clock
```

## `[example]`   

Any name works above in the brackets, just add it to the `[goals]` block.

| Key                  | Value | Description|
|----------------------|------|-----|
| `rulea` | `<int>` | Pick a value for one of the rules listed below. |
| `ruleb` | `<int>` | Pick a value that makes sense for rulea. |
| `arga` | `<int>` | Optional value that depends on rulea. | 
| `argb` | `<int>` | Optional value that depends on rulea. | 
| `type` | `<int>` | Pick the type of comparison to be applied. | 
| `value` | `<int>`| Pick the value to compare the rule against. | 
| `text` | `<int>` | Insert the string ID for the rule. | 
| `sticky` | `<int>` | Pick either 0 or 1. | 
| `hidden` | `<int>` | Pick either 0 or 1. | 
| `optional` | `<int>` | Pick either 0 or 1. |   
| `trulea` | `<int>` | Pick a value for one of the triggers. |
| `truleb` | `<int>` | Pick a value that makes sense for trulea. |
| `targa` | `<int>` | Optional argument for the trigger. | 
| `targb` | `<int>` | Optional argument for the trigger. | 

### Rule 0 (rulea = 0): Costs and profits

When `rulea == 0`:

- `arga` (Period) - `0` monthly, `1` yearly, `2` total
- `argb` (Unused)
  - `0` food cost
  - `1` healing cost
  - `2` purchase cost
  - `3` construction cost
  - `4` admissions
  - `5` admissions income
  - `6` food income
  - `7` drink income
  - `8` donations income
  - `9` construction refund
  - `10` animal refund
  - `11` keeper wages
  - `12` guide wages
  - `13` maint wages
  - `14` net income
  - `15` zoo value

### Rule 1 (rulea = 1): Counts and ratings
- `arga` (Month)
- `argb` (Unused)
- The `value` returned is clamped to `0` until the month is after `arga`.
    - `0` animal rating
    - `1` guest rating
    - `2` zoo rating
    - `3` num guests
    - `4` num animals
    - `5` num sick animals
    - `6` num species
    - `7` available cash


### Rule 2 (rulea = 2)
- `arga` (Animal Name ID)
- `argb` (Subtype) - 0 male, 1 female, 3 young (2, pregnant is obsolete)
- `value` - `number`
  - 0 match type
  - 1 match subtype
  - 2 match type and subtype
  - 3 match type or subtype


### Rule 3 (rulea = 3)
- `arga` (Unused or Habitat Rating)
- `argb` (Unused or Animal Name ID)
  - 0 num habitats
  - 1 num non-empty habitats


### Rule 4 (rulea = 4)
- `arga` (ID)
- `argb` (ID or Unused)
  - 0 Family
  - 1 Genus
  - 2 Species
  - 3 Location
  - 4 Habitat Type
  - 5 Family (`arga`) and Location (`argb`)
  - 6 Genus (`arga`) and Location (`argb`)
  - 7 Family (`arga`) and Habitat Type (`argb`)
  - 8 Genus (`arga`) and Habitat Type (`argb`)
  - 9 Habitat Type (`arga`) and Location (`argb`)
  - 10 Number of boxed animals


### Rule 5 (rulea = 5)
- `arga` (ID or Unused)
- `argb` (Unused)
  - 0 Have a rating of '`value`' for all habitats.
  - 1 Have a rating of '`value`' for all family '`arga`' habitats.
  - 2 Have a rating of '`value`' for all genus '`arga`' habitats.
  - 3 Have a rating of '`value`' for all species '`arga`' habitats.
  - 4 Have a rating of '`value`' for all location '`arga`' habitats.
  - 5 Have a rating of '`value`' for all era '`arga`' habitats.
  - 6 Have a rating of '`value`' for all habitat type '`arga`' habitats.

### Rule 6 (rulea = 6)
```INI
;; arga (Number of Habitats)
;; argb (ID or Unused)
; 0 Have a rating of 'value' for 'arga' habitats.
; 1 Have a rating of 'value' for 'arga' family 'argb' habitats.
; 2 Have a rating of 'value' for 'arga' genus 'argb' habitats.
; 3 Have a rating of 'value' for 'arga' species 'argb' habitats.
; 4 Have a rating of 'value' for 'arga' location 'argb' habitats.
; 5 Have a rating of 'value' for 'arga' era 'argb' habitats.
; 6 Have a rating of 'value' for 'arga' habitat type 'argb' habitats.
```

### Rule 7 (rulea = 7)
```INI
;; arga (Unused)
;; argb (Unused)
; 0 Current month value (0 is beginning of the game, 1-12)
; 1 Current year value.
; 2 Number of months that have passed ((12 * year) + month)
```

### Rule 8 (rulea = 8)
```INI
;; arga (ID)
;; argb (Unused)
; 0 Returns value if entity type arga is available.
```

### Rule 9 (rulea = 9)
```INI
;; arga (Unused)
;; argb (Unused)
;; 0 Returns number of goals in progress.
;; 1 Returns number of goals completed.
;; 2 Returns number of goals failed.
```

### Rule 10 (rulea = 10)
```INI
;; arga (ID of UI element)
;; 0 Returns value if the element is currently shown.
;; 1 Returns value if the element is triggered.
```

### Rule 11 (rulea = 11)
```INI
;; arga (ID of listbox UI element)
;; value = 0 (1st listbox element)
;; value = 1 (2nd listbox element), etc.
;; type = 2
```

### Types - Determines how the rule and value are compared.
- 0 Goal completed when rule >= value.
- 1 Goal completed when rule <  value.
- 2 Goal completed when rule == value.
- 3 Goal failed when rule >= value.
- 4 Goal failed when rule <  value.
- 5 Goal failed when rule == value.
- 6 Goal completed when rule >= value, else failed.
- 7 Goal completed when rule <  value, else failed.
- 8 Goal completed when rule == value, else failed.

### Sticky - Determines if the rule stays completed or failed once there.
- 0 - Can be completed or failed at times, but can slip back to in progress.
- 1 - Once completed or failed, is always completed or failed.

### Hidden - Determines if the goal is displayed to the player.
- 0 - Shown to the player.
- 1 - Not shown to the player.

### Optional - Determines if the goal must be met to complete the scenario.
- 0 - Not optional, goal must be met.
- 1 - Optional, goal can be failed or completed without affecting scenario.

### Trigger 0 (trulea = 0)
- targa (Unused)
- targb (Unused)
- 0 Do nothing.

### Trigger 1 (trulea = 1)
- targa (Resource ID of message)
- targb (Arg passed to the message.)
- 0 Send info message.
- 1 Send good message.
- 2 Send high priority message.

```INI
; Trigger 2 (trulea = 2)
; targa (Varies)
; targb (Varies)
; Rules 1,3,5,7,9 have been made obsolete but still work.
; To fix them, replace the old rule by adding 1 - for example, 1 becomes 2.
;  0 Popup dialog.                  (targa layout ID,  targb unused)
;  2 Popup and click UI element.    (targa ele ID, targb layout if > 0)
;  4 Popup and disable UI element.  (targa ele ID, targb layout if > 0)
;  6 Popup and enable UI element.   (targa ele ID, targb layout if > 0)
;  8 Popup and hide UI element.     (targa ele ID, targb layout if > 0)
; 10 Popup and show UI element.     (targa ele ID, targb layout if > 0)
; 11 Popup any layout.              (targa layout ID,  targb pause flag)
; 12 Disable block of UI elements.  (targa block, targb layout if > 0)
; 13 Enable block of UI elements.   (targa block, targb layout if > 0)
; 14 Hide block of UI elements.     (targa block, targb layout if > 0)
; 15 Show block of UI elements.     (targa block, targb layout if > 0)
; 16 Set block of UI elements.      (targa block, targb layout if > 0)
; For 16, the entries in the block are <id>=enable,disable,hide,show
```

```INI
; Trigger 3 (trulea = 3)
; targa (Amount of cash.)
; targb (Unused or resource ID for message - use %s to capture dollar amount.)
; 0 Donate cash. (Shows up in donations column.)
; 1 Add cash. (Doesn't show up in finance sheet.)
; 2 Set cash. (Brute force sets the cash amount.)
```

```INI
; Trigger 4 (trulea = 4)
; targa (ID of entity type)
; targb (Unused or ID of message.)
;  0 Make entity type available.
;  1 Make entity type unavailable.
;  2 Make entity type available and display UI message targb.
;  3 Make entity type unavailable and display UI message targb.
;  4 Make entity type available and display popup targb.
;  5 Make entity type unavailable and display popup targb.
;  6 Make all animals available.
;  7 Make all animals unavailable.
;  8 Make all things available.
;  9 Make all things unavailable.
```

```INI
; Trigger 5 (trulea = 5)
; targa (ID of entity type.)
; targb (ID of message - no message if <= 0.)
; 0 Add boxed animal of type targa to zoo, subtype "m".
; 1 Add boxed animal of type targa to zoo, subtype "f".
; 2 Add boxed animal of type targa to zoo, subtype "y".
```

```INI
; Trigger 6 (trulea = 6)
; targa (ID of award)
; targb (ID of message - no message if <= 0)
; 0 Present an award to the zoo
```

```INI
; Trigger 7 (trulea = 7)
; targa (ID of sub block)
; targb (Unused or ID of message.)
;  0 Make entity type available.
;  1 Make entity type unavailable.
;  2 Make entity type available and display UI message targb.
;  3 Make entity type unavailable and display UI message targb.
;  4 Make entity type available and display popup targb.
;  5 Make entity type unavailable and display popup targb.
```

## `[goals]`

This category is not documented.

Example code under this category:

```INI
goal=test
;goal=500
;goal=501
;goal=602
;goal=603
;goal=trigger 2 example a
;goal=trigger 2 example b
;goal=trigger 7 example
```

Example goal after defining it above:

```INI
[test]
rulea=6
ruleb=5
arga=3
argb=9623
value=80
hidden=0
optional=0
sticky=0
type=0
text=17605
```

## Misc categories and properties

Have a rating of 50 for all habitats.

```INI
[500]
rulea=5
ruleb=0
value=50
text=17500```

Have a rating of 50 for all Cat habitats.

```INI
[501]
rulea=5
ruleb=1
arga=5206
value=50
text=17501```

Have a rating of 50 for 3 or more Tiger habitats.

```INI
[602]
rulea=6
ruleb=2
arga=3
argb=5107
value=50
text=17602```

Have a rating of 50 for 3 or more Bengal Tiger habitats.

```INI
[603]
rulea=6
ruleb=3
arga=3
argb=5007
value=50
text=17603
```