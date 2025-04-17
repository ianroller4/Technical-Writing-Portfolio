# Style Guide for Godot

## Files and Folders


## Naming Conventions

- Classes: PascalCase
```gdscript
class_name PlayerController
```
- Variables: camelCase
```gdscript
var itemCount := 0
```
- Functions: snake_case
```gdscript
func move_player():
    ...
```  
- Constants: ALL_CAPS
```gdscript
const MAX_HEALTH := 3
```
- Signals: camelCase
```gdscript
signal playerHit
```

## Script Organization
- Variables / signals group together based on need
- ready function, if needed
- physics function, if needed
- Input related functions
- group functions by need, all support function should be above the function that calls them unless in one of the three function groups mentioned

## General Programming
- Use match if discrite possiblities
- Use if for ranges or inequalities
- only one return per function
- always use : *type* to declare that a variable must be that type
- onready var should be considered constants and thus use their naming convention
- Name classes
- if a function returns declare return type
- if a premade function parameter is not used add an _ before the name ie _delta
- loop should use i, j, and k in that order unless a better name is available

## Input Reading
- If not needing to be checked every frame then check should not be in physics
- Use Input function for things not needing to be called every frame

## Global Files
- Use sparingly
- Use for storing variables that need to be accessed by multiple scripts
- Use for functionality not related to gameplay but has multiple scripts using its functionality (ie save load)
- Use for passing information when changing scenes
- Do not make everything global only what is needed to be

## Comments and Documentation
- All created functions should be documented with purpose, parameters, and any returns
- Variable / signal groups should be labeled with a """ """ comment

## Miscellaneous
