# PaperScope

The `PaperScope` class represents the scope associated with a Paper context. When working with PaperScript, these scopes are automatically created for us, and through clever scoping the properties and methods of the active scope seem to become part of the global scope.

When working with normal JavaScript code, `PaperScope` objects need to be manually created and handled.

Paper classes can only be accessed through `PaperScope` objects. Thus in PaperScript they are global, while in JavaScript, they are available on the global `paper` object. For JavaScript you can use `paperScope.install(scope)` to install the Paper classes and objects on the global scope. Note that when working with more than one scope, this still works for classes, but not for objects like `paperScope.project`, since they are not updated in the injected scope if scopes are switched.

The global `paper` object is simply a reference to the currently active `PaperScope`.

## Constructors

*   `PaperScope()`

    Creates a PaperScope object.

    * Returns:
    * `PaperScope`

## Properties

*   `version`

    The version of Paper.js, as a string.

    Read only.

    * Type:
    * `String`
*   `settings`

    Gives access to paper’s configurable settings.

    * Type:
    * `Object`
    * Options:
    * `settings.insertItems: Boolean` — controls whether newly created items are automatically inserted into the scene graph, by adding them to `project.activeLayer` — default: `true`
    * `settings.applyMatrix: Boolean` — controls what value newly created items have their `item.applyMatrix` property set to (Note that not all items can set this to `false`) — default: `true`
    * `settings.handleSize: Number` — the size of the curve handles when drawing selections — default: `4`
    * `settings.hitTolerance: Number` — the default tolerance for hit- tests, when no value is specified — default: `0`
*   `project`

    The currently active project.

    * Type:
    * `Project`
*   `projects`

    The list of all open projects within the current Paper.js context.

    * Type:
    * Array of `Project` objects
*   `view`

    The reference to the active project’s view.

    Read only.

    * Type:
    * `View`
*   `tool`

    The reference to the active tool.

    * Type:
    * `Tool`
*   `tools`

    The list of available tools.

    * Type:
    * Array of `Tool` objects

## Methods

*   `execute(code[, options])`

    Compiles the PaperScript code into a compiled function and executes it. The compiled function receives all properties of this `PaperScope` as arguments, to emulate a global scope with unaffected performance. It also installs global view and tool handlers automatically on the respective objects.

    * Options:
    * `options.url: String` — the url of the source, for source-map debugging
    * `options.source: String` — the source to be used for the source- mapping, in case the code that’s passed in has already been mingled.
    * Parameters:
    * `code:` `String` — the PaperScript code
    * `options:` `Object` — the compilation options — optional
*   `install(scope)`

    Injects the paper scope into any other given scope. Can be used for example to inject the currently active PaperScope into the window’s global scope, to emulate PaperScript-style globally accessible Paper classes and objects.

    **Please note:** Using this method may override native constructors (e.g. Path). This may cause problems when using Paper.js in conjunction with other libraries that rely on these constructors. Keep the library scoped if you encounter issues caused by this.

    * Parameters:
    * `scope:`

    Example:

    ```
    paper.install(window);
    ```
*   `setup(element)`

    Sets up an empty project for us. If a canvas is provided, it also creates a `View` for it, both linked to this scope.

    * Parameters:
    * `element:` `HTMLCanvasElement`⟋`String`⟋`Size` — the HTML canvas element this scope should be associated with, or an ID string by which to find the element, or the size of the canvas to be created for usage in a web worker.
*   `activate()`

    Activates this PaperScope, so all newly created items will be placed in its active project.

## Static Methods

*   `PaperScope.get(id)`

    Retrieves a PaperScope object with the given scope id.

    * Parameters:
    * `id:`
    * Returns:
    * `PaperScope`
