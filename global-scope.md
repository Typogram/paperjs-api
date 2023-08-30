# Global Scope

When code is executed as PaperScript, the script’s scope is populated with all fields of the currently active `PaperScope` object, which within the script appear to be global.

In a JavaScript context, only the `paper` variable is added to the global scope, referencing the currently active `PaperScope` object, through which all properties and Paper.js classes can be accessed.

## Properties

*   `paper`

    A reference to the currently active `PaperScope` object.

    * Type:
    * `PaperScope`

### Global PaperScript Properties

*   `project`

    The project for which the PaperScript is executed.

    Note that when working with multiple projects, this does not necessarily reflect the currently active project. For this, use `paperScope.project` instead.

    * Type:
    * `Project`
*   `projects`

    The list of all open projects within the current Paper.js context.

    * Type:
    * Array of `Project` objects
*   `view`

    The reference to the project’s view.

    Note that when working with multiple projects, this does not necessarily reflect the view of the currently active project. For this, use `paperScope.view` instead.

    Read only.

    * Type:
    * `View`
*   `tool`

    The reference to the tool object which is automatically created when global tool event handlers are defined.

    Note that when working with multiple tools, this does not necessarily reflect the currently active tool. For this, use `paperScope.tool` instead.

    * Type:
    * `Tool`
*   `tools`

    The list of available tools.

    * Type:
    * Array of `Tool` objects

### PaperScript View Event Handlers

*   `onFrame`

    A global reference to the `view.onFrame` handler function.

    * Type:
    * `Function`
*   `onResize`

    A reference to the `view.onResize` handler function.

    * Type:
    * `Function`

### PaperScript Tool Event Handlers

*   `onMouseDown`

    A reference to the `tool.onMouseDown` handler function.

    * Type:
    * `Function`
*   `onMouseDrag`

    A reference to the `tool.onMouseDrag` handler function.

    * Type:
    * `Function`
*   `onMouseMove`

    A reference to the `tool.onMouseMove` handler function.

    * Type:
    * `Function`
*   `onMouseUp`

    A reference to the `tool.onMouseUp` handler function.

    * Type:
    * `Function`

### Keyboard Event Handlers (for PaperScript)

*   `onKeyDown`

    A reference to the `tool.onKeyDown` handler function.

    * Type:
    * `Function`
*   `onKeyUp`

    A reference to the `tool.onKeyUp` handler function.

    * Type:
    * `Function`
