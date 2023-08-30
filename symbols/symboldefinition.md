# SymbolDefinition

Symbols allow you to place multiple instances of an item in your project. This can save memory, since all instances of a symbol simply refer to the original item and it can speed up moving around complex objects, since internal properties such as segment lists and gradient positions don’t need to be updated with every transformation.

## Constructors

*   `SymbolDefinition(item[, dontCenter])`

    Creates a Symbol definition.

    * Parameters:
    * `item:` `Item` — the source item which is removed from the scene graph and becomes the symbol’s definition.
    * `dontCenter:` `Boolean` — optional, default: `false`
    * Returns:
    * `SymbolDefinition`

    Example:Placing 100 instances of a symbol:

    ```jsx
    var path = new Path.Star(new Point(0, 0), 6, 5, 13);
    path.style = {
        fillColor: 'white',
        strokeColor: 'black'
    };

    // Create a symbol definition from the path:
    var definition = new SymbolDefinition(path);

    // Place 100 instances of the symbol definition:
    for (var i = 0; i < 100; i++) {
        // Place an instance of the symbol definition in the project:
        var instance = definition.place();

        // Move the instance to a random position within the view:
        instance.position = Point.random() * view.size;

        // Rotate the instance by a random amount between
        // 0 and 360 degrees:
        instance.rotate(Math.random() * 360);

        // Scale the instance between 0.25 and 1:
        instance.scale(0.25 + Math.random() * 0.75);
    }
    ```

## Properties

*   `project`

    The project that this symbol belongs to.

    Read only.

    * Type:
    * `Project`
*   `item`

    The item used as the symbol’s definition.

    * Type:
    * `Item`

## Methods

*   `place([position])`

    Places in instance of the symbol in the project.

    * Parameters:
    * `position:` `Point` — the position of the placed symbol — optional
    * Returns:
    * `SymbolItem`
*   `clone()`

    Returns a copy of the symbol.

    * Returns:
    * `SymbolDefinition`
*   `equals(symbol)`

    Checks whether the symbol’s definition is equal to the supplied symbol.

    * Parameters:
    * `symbol:` `SymbolDefinition`
    * Returns:
    * `Boolean` — `true` if they are equal, `false` otherwise
