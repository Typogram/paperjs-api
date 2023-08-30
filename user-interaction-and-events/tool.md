# Tool

The Tool object refers to a script that the user can interact with by using the mouse and keyboard and can be accessed through the global `tool` variable. All its properties are also available in the paper scope.

The global `tool` variable only exists in scripts that contain mouse handler functions (`onMouseMove`, `onMouseDown`, `onMouseDrag`, `onMouseUp`) or a keyboard handler function (`onKeyDown`, `onKeyUp`).

Example:

```jsx
var path;

// Only execute onMouseDrag when the mouse
// has moved at least 10 points:
tool.minDistance = 10;

tool.onMouseDown = function(event) {
    // Create a new path every time the mouse is clicked
    path = new Path();
    path.add(event.point);
    path.strokeColor = 'black';
}

tool.onMouseDrag = function(event) {
    // Add a point to the path every time the mouse is dragged
    path.add(event.point);
}
```

## Properties

*   `minDistance`

    The minimum distance the mouse has to drag before firing the onMouseDrag event, since the last onMouseDrag event.

    * Type:
    * `Number`
*   `maxDistance`

    The maximum distance the mouse has to drag before firing the onMouseDrag event, since the last onMouseDrag event.

    * Type:
    * `Number`
* `fixedDistance`
  * Type:
  * `Number`

### Mouse Event Handlers

*   `onMouseDown`

    The function to be called when the mouse button is pushed down. The function receives a `ToolEvent` object which contains information about the tool event.

    * Type:
    * `Function`⟋`null`

    Example:Creating circle shaped paths where the user presses the mouse button:

    ```jsx
    tool.onMouseDown = function(event) {
        // Create a new circle shaped path with a radius of 10
        // at the position of the mouse (event.point):
        var path = new Path.Circle({
            center: event.point,
            radius: 10,
            fillColor: 'black'
        });
    }
    ```
*   `onMouseDrag`

    The function to be called when the mouse position changes while the mouse is being dragged. The function receives a `ToolEvent` object which contains information about the tool event.

    * Type:
    * `Function`⟋`null`

    Example:Draw a line by adding a segment to a path on every mouse drag event:

    ```jsx
    // Create an empty path:
    var path = new Path({
        strokeColor: 'black'
    });

    tool.onMouseDrag = function(event) {
        // Add a segment to the path at the position of the mouse:
        path.add(event.point);
    }
    ```
*   `onMouseMove`

    The function to be called the mouse moves within the project view. The function receives a `ToolEvent` object which contains information about the tool event.

    * Type:
    * `Function`⟋`null`

    Example:Moving a path to the position of the mouse:

    ```jsx
    // Create a circle shaped path with a radius of 10 at {x: 0, y: 0}:
    var path = new Path.Circle({
        center: [0, 0],
        radius: 10,
        fillColor: 'black'
    });

    tool.onMouseMove = function(event) {
        // Whenever the user moves the mouse, move the path
        // to that position:
        path.position = event.point;
    }
    ```
*   `onMouseUp`

    The function to be called when the mouse button is released. The function receives a `ToolEvent` object which contains information about the tool event.

    * Type:
    * `Function`⟋`null`

    Example:Creating circle shaped paths where the user releases the mouse:

    ```jsx
    tool.onMouseUp = function(event) {
        // Create a new circle shaped path with a radius of 10
        // at the position of the mouse (event.point):
        var path = new Path.Circle({
            center: event.point,
            radius: 10,
            fillColor: 'black'
        });
    }
    ```

### Keyboard Event Handlers

*   `onKeyDown`

    The function to be called when the user presses a key on the keyboard. The function receives a `KeyEvent` object which contains information about the keyboard event.

    If the function returns `false`, the keyboard event will be prevented from bubbling up. This can be used for example to stop the window from scrolling, when you need the user to interact with arrow keys.

    * Type:
    * `Function`⟋`null`

    Example:Scaling a path whenever the user presses the space bar:

    ```jsx
    // Create a circle shaped path:
        var path = new Path.Circle({
            center: new Point(50, 50),
            radius: 30,
            fillColor: 'red'
        });

    tool.onKeyDown = function(event) {
        if (event.key == 'space') {
            // Scale the path by 110%:
            path.scale(1.1);

            // Prevent the key event from bubbling
            return false;
        }
    }
    ```
*   `onKeyUp`

    The function to be called when the user releases a key on the keyboard. The function receives a `KeyEvent` object which contains information about the keyboard event.

    If the function returns `false`, the keyboard event will be prevented from bubbling up. This can be used for example to stop the window from scrolling, when you need the user to interact with arrow keys.

    * Type:
    * `Function`⟋`null`

    Example:

    ```jsx
    tool.onKeyUp = function(event) {
        if (event.key == 'space') {
            console.log('The spacebar was released!');
        }
    }
    ```

## Methods

*   `activate()`

    Activates this tool, meaning `paperScope.tool` will point to it and it will be the one that receives tool events.
*   `remove()`

    Removes this tool from the `paperScope.tools` list.

### Event Handling

*   `on(type, function)`

    Attach an event handler to the tool.

    * Parameters:
    * `type:` `String` — the event type: `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘mousemove’`, `‘keydown’`, `‘keyup’`
    * `function:` `Function` — the function to be called when the event occurs, receiving a `ToolEvent` object as its sole argument
    * Returns:
    * `Tool` — this tool itself, so calls can be chained
*   `on(param)`

    Attach one or more event handlers to the tool.

    * Parameters:
    * `param:` `Object` — an object literal containing one or more of the following properties: `mousedown`, `mouseup`, `mousedrag`, `mousemove`, `keydown`, `keyup`
    * Returns:
    * `Tool` — this tool itself, so calls can be chained
*   `off(type, function)`

    Detach an event handler from the tool.

    * Parameters:
    * `type:` `String` — the event type: `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘mousemove’`, `‘keydown’`, `‘keyup’`
    * `function:` `Function` — the function to be detached
    * Returns:
    * `Tool` — this tool itself, so calls can be chained
*   `off(param)`

    Detach one or more event handlers from the tool.

    * Parameters:
    * `param:` `Object` — an object literal containing one or more of the following properties: `mousedown`, `mouseup`, `mousedrag`, `mousemove`, `keydown`, `keyup`
    * Returns:
    * `Tool` — this tool itself, so calls can be chained
*   `emit(type, event)`

    Emit an event on the tool.

    * Parameters:
    * `type:` `String` — the event type: `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘mousemove’`, `‘keydown’`, `‘keyup’`
    * `event:` `Object` — an object literal containing properties describing the event
    * Returns:
    * `Boolean` — `true` if the event had listeners, `false` otherwise
*   `responds(type)`

    Check if the tool has one or more event handlers of the specified type.

    * Parameters:
    * `type:` `String` — the event type: `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘mousemove’`, `‘keydown’`, `‘keyup’`
    * Returns:
    * `Boolean` — `true` if the tool has one or more event handlers of the specified type, `false` otherwise
