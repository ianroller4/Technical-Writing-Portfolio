# Style Guide for Godot

## Table of Contents
- [Naming Conventions](#naming-conventions)
- [Script Organization](#script-organization)
- [General Programming](#general-programming)
  - [Variables](#variables)
  - [Functions](#functions)
  - [Loops](#loops)
  - [Input Handling](#input-handling)
- [Global Files](#global-files)
- [Comments and Documentation](#comments-and-documentation)


## Naming Conventions 

### Files
- Scenes: PascalCase
  - OverWorld.tscn
- Scripts: camelCase
  - gameController.gd

### Variables and Functions
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
>A script's contents should ordered in the following way
1. Variables, constants, and signals 
    - These should be grouped together by their purpose, for example:
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
2. The `_ready()`, `_process(...)`, and `_physics_process(...)` functions, if needed
    ```gdscript
    func _ready():
        # Functions and variables to be set up upon entering scene are called here
        ...

    func _process(delta):
        # Functions that do not require to be called at a fixed rate are called here
        ...

    func _physics_process(delta):
        # Functions that needed to be called at a fixed rate are called here
        ...
    ```
3. Input handling functions, if needed
    ```gdscript
    func _input(event):
        # Inputs that do not need to be checked for constantly
        ...
    ```
4. All other functions
    - Any functions that are called in another function should be placed before the function in which they are called, for example:
        ```gdscript
        func get_input_direction():
            ...

        func move():
            get_input_direction()
            ...
        ```

## General Programming
### Variables
- Always declare the type of a variable
    ```gdscript
    # For when setting the variable
    var count := 0

    # For when setting the variable later
    var count : int
    ```
- Treat `@onready` variables like constants when used to reference nodes
    ```gdscript
    @onready var SCORE := $Score
    ```
### Functions
- Functions that return should
  - Declare the return type
  - Have only one return statement at the end of the function
    ```gdscript
    func get_count() -> int:

        ...

        return count
    ```
- Functions with parameters should declare the type of each parameter
  ```gdscript
  func add(a : int, b : int) -> int:
    
    ...

    return sum
  ```
- Unused parameters in engine-defined functions should be preceded with an underscore
    ```gdscript
    func _physics_process(_delta):
        ...
    ```

### Loops
- For loops should use the i, j, and k as looping variables in that order for nested loops, unless another variable name would make the code easier to read
    ```gdscript
    for i in level:
        for j in row:
            for k in col:
                ...
    ```

### Input Handling
- Input not required to be check for consistantly should be handled by `_input(...)`
    ```gdscript
    func _input(event)
        ...
    ```

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
- Comments for a line of code should come before the code and have a space after '#'
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
