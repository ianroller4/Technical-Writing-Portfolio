# Style Guide for Godot

## Naming Conventions

- Scenes: PascalCase
  - OverWorld.tscn
- Scripts: camelCase
  - gameController.gd

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
> Global files (also called singletons or autoloads) should only be used when necessary to prevent loading unnecessary data
### When and What to Use a Global File
- Use for functionality used by multiple different unconnected scenes
  - Ex. Saving and loading functions
- Use for passing necessary data between scenes
- Use for storing data that will be required in multiple scenes

## Comments and Documentation
- All user created functions should be documented by doing the following:
```gdscript
"""
Purpose:
    Purpose of the function
Parameters:
    Parameter 1: type and what it is
    ...
    Parameter n: type and what it is
Return:
    What the function returns and its type
"""
```
- Variables, constants, and signals once grouped together should be labeled 
```gdscript
""" Speed """
const DASH_SPEED := 200
const WALK_SPEED := 100
var speed := WALK_SPEED

""" Health """
var health := 3
signal tookDamage

...
```
- Comments for a line of code should come before the code
```gdscript
# Increase enemy count
enemyCount += 1
```
- For comments that are more than one line use block comments
```gdscript
"""
This is a block comment.
Comments can be on multiple lines.
"""
```
