# View

The View object wraps an HTML element and handles drawing and user interaction through mouse and keyboard for it. It offer means to scroll the view, find the currently visible bounds in project coordinates, or the center, both useful for constructing artwork that should appear centered on screen.

## Properties

*   `autoUpdate`

    Controls whether the view is automatically updated in the next animation frame on changes, or whether you prefer to manually call `update`() or `requestUpdate`() after changes. Note that this is `true` by default, except for Node.js, where manual updates make more sense.

    * Type:
    * `Boolean`
*   `element`

    The underlying native element.

    Read only.

    * Type:
    * `HTMLCanvasElement`
*   `pixelRatio`

    The ratio between physical pixels and device-independent pixels (DIPs) of the underlying canvas / device. It is `1` for normal displays, and `2` or more for high-resolution displays.

    Read only.

    * Type:
    * `Number`
*   `resolution`

    The resoltuion of the underlying canvas / device in pixel per inch (DPI). It is `72` for normal displays, and `144` for high-resolution displays with a pixel-ratio of `2`.

    Read only.

    * Type:
    * `Number`
*   `viewSize`

    The size of the view. Changing the view’s size will resize it’s underlying element.

    * Type:
    * `Size`
*   `bounds`

    The bounds of the currently visible area in project coordinates.

    Read only.

    * Type:
    * `Rectangle`
*   `size`

    The size of the visible area in project coordinates.

    Read only.

    * Type:
    * `Size`
*   `center`

    The center of the visible area in project coordinates.

    * Type:
    * `Point`
*   `zoom`

    The view’s zoom factor by which the project coordinates are magnified.

    * Type:
    * `Number`
    * See also:
    * `scaling`
*   `rotation`

    The current rotation angle of the view, as described by its `matrix`.

    * Type:
    * `Number`
*   `scaling`

    The current scale factor of the view, as described by its `matrix`.

    * Type:
    * `Point`
    * See also:
    * `zoom`
*   `matrix`

    The view’s transformation matrix, defining the view onto the project’s contents (position, zoom level, rotation, etc).

    * Type:
    * `Matrix`

### Event Handlers

*   `onFrame`

    Handler function to be called on each frame of an animation. The function receives an event object which contains information about the frame event:

    * Type:
    * `Function`⟋`null`
    * Options:
    * `event.count: Number` — the number of times the frame event was fired
    * `event.time: Number` — the total amount of time passed since the first frame event in seconds
    * `event.delta: Number` — the time passed in seconds since the last frame event
    * See also:
    * `item.onFrame`

    Example:Creating an animation:

    ```jsx
    // Create a rectangle shaped path with its top left point at:
    // {x: 50, y: 25} and a size of {width: 50, height: 50}
    var path = new Path.Rectangle(new Point(50, 25), new Size(50, 50));
    path.fillColor = 'black';

    view.onFrame = function(event) {
        // Every frame, rotate the path by 3 degrees:
        path.rotate(3);
    }
    ```
*   `onResize`

    Handler function that is called whenever a view is resized.

    * Type:
    * `Function`⟋`null`

    Example:Repositioning items when a view is resized:

    ```jsx
    // Create a circle shaped path in the center of the view:
    var path = new Path.Circle(view.bounds.center, 30);
    path.fillColor = 'red';

    view.onResize = function(event) {
        // Whenever the view is resized, move the path to its center:
        path.position = view.center;
    }
    ```
*   `onMouseDown`

    The function to be called when the mouse button is pushed down on the view. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onMouseDown`
*   `onMouseDrag`

    The function to be called when the mouse position changes while the mouse is being dragged over the view. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onMouseDrag`
*   `onMouseUp`

    The function to be called when the mouse button is released over the item. The function receives a `MouseEvent` object which contains information about the mouse event.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onMouseUp`
*   `onClick`

    The function to be called when the mouse clicks on the view. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onClick`
*   `onDoubleClick`

    The function to be called when the mouse double clicks on the view. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onDoubleClick`
*   `onMouseMove`

    The function to be called repeatedly while the mouse moves over the view. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onMouseMove`
*   `onMouseEnter`

    The function to be called when the mouse moves over the view. This function will only be called again, once the mouse moved outside of the view first. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `item.onMouseEnter`
*   `onMouseLeave`

    The function to be called when the mouse moves out of the view. The function receives a `MouseEvent` object which contains information about the mouse event. Note that such mouse events bubble up the scene graph hierarchy, reaching the view at the end, unless they are stopped before with `event.stopPropagation`() or by returning `false` from a handler.

    * Type:
    * `Function`⟋`null`
    * See also:
    * `view.onMouseLeave`

## Methods

*   `remove()`

    Removes this view from the project and frees the associated element.
*   `update()`

    Updates the view if there are changes. Note that when using built-in event hanlders for interaction, animation and load events, this method is invoked for you automatically at the end.

    * Returns:
    * `Boolean` — `true` if the view was updated, `false` otherwise
*   `requestUpdate()`

    Requests an update of the view if there are changes through the browser’s requestAnimationFrame() mechanism for smooth animation. Note that when using built-in event handlers for interaction, animation and load events, updates are automatically invoked for you automatically at the end.
*   `play()`

    Makes all animation play by adding the view to the request animation loop.
*   `pause()`

    Makes all animation pause by removing the view from the request animation loop.
*   `isVisible()`

    Checks whether the view is currently visible within the current browser viewport.

    * Returns:
    * `Boolean` — `true` if the view is visible, `false` otherwise
*   `isInserted()`

    Checks whether the view is inserted into the browser DOM.

    * Returns:
    * `Boolean` — `true` if the view is inserted, `false` otherwise

### Transform Functions

*   `translate(delta)`

    Translates (scrolls) the view by the given offset vector.

    * Parameters:
    * `delta:` `Point` — the offset to translate the view by
*   `rotate(angle[, center])`

    Rotates the view by a given angle around the given center point.

    Angles are oriented clockwise and measured in degrees.

    * Parameters:
    * `angle:` `Number` — the rotation angle
    * `center:` `Point` — optional, default: `view.center`
    * See also:
    * `matrix.rotate(angle[, center])`
*   `scale(scale[, center])`

    Scales the view by the given value from its center point, or optionally from a supplied point.

    * Parameters:
    * `scale:` `Number` — the scale factor
    * `center:` `Point` — optional, default: `view.center`
*   `scale(hor, ver[, center])`

    Scales the view by the given values from its center point, or optionally from a supplied point.

    * Parameters:
    * `hor:` `Number` — the horizontal scale factor
    * `ver:` `Number` — the vertical scale factor
    * `center:` `Point` — optional, default: `view.center`
*   `shear(shear[, center])`

    Shears the view by the given value from its center point, or optionally by a supplied point.

    * Parameters:
    * `shear:` `Point` — the horizontal and vertical shear factors as a point
    * `center:` `Point` — optional, default: `view.center`
    * See also:
    * `matrix.shear(shear[, center])`
*   `shear(hor, ver[, center])`

    Shears the view by the given values from its center point, or optionally by a supplied point.

    * Parameters:
    * `hor:` `Number` — the horizontal shear factor
    * `ver:` `Number` — the vertical shear factor
    * `center:` `Point` — optional, default: `view.center`
    * See also:
    * `matrix.shear(hor, ver[, center])`
*   `skew(skew[, center])`

    Skews the view by the given angles from its center point, or optionally by a supplied point.

    * Parameters:
    * `skew:` `Point` — the horizontal and vertical skew angles in degrees
    * `center:` `Point` — optional, default: `view.center`
    * See also:
    * `matrix.shear(skew[, center])`
*   `skew(hor, ver[, center])`

    Skews the view by the given angles from its center point, or optionally by a supplied point.

    * Parameters:
    * `hor:` `Number` — the horizontal skew angle in degrees
    * `ver:` `Number` — the vertical sskew angle in degrees
    * `center:` `Point` — optional, default: `view.center`
    * See also:
    * `matrix.shear(hor, ver[, center])`
*   `transform(matrix)`

    Transform the view.

    * Parameters:
    * `matrix:` `Matrix` — the matrix by which the view shall be transformed
*   `projectToView(point)`

    Converts the passed point from project coordinate space to view coordinate space, which is measured in browser pixels in relation to the position of the view element.

    * Parameters:
    * `point:` `Point` — the point in project coordinates to be converted
    * Returns:
    * `Point` — the point converted into view coordinates
*   `viewToProject(point)`

    Converts the passed point from view coordinate space to project coordinate space.

    * Parameters:
    * `point:` `Point` — the point in view coordinates to be converted
    * Returns:
    * `Point` — the point converted into project coordinates
*   `getEventPoint(event)`

    Determines and returns the event location in project coordinate space.

    * Parameters:
    * `event:` `Event` — the native event object for which to determine the location.
    * Returns:
    * `Point` — the event point in project coordinates.

### Event Handling

*   `on(type, function)`

    Attach an event handler to the view.

    * Parameters:
    * `type:` `String` — the type of event: `‘frame’`, `‘resize’`, `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘click’`, `‘doubleclick’`, `‘mousemove’`, `‘mouseenter’`, `‘mouseleave’`
    * `function:` `Function` — the function to be called when the event occurs, receiving a `MouseEvent` or `Event` object as its sole argument
    * Returns:
    * `View` — this view itself, so calls can be chained

    Example:Create a rectangle shaped path with its top left point at: {x: 50, y: 25} and a size of {width: 50, height: 50}

    ```jsx
    var path = new Path.Rectangle(new Point(50, 25), new Size(50, 50));
    path.fillColor = 'black';

    var frameHandler = function(event) {
        // Every frame, rotate the path by 3 degrees:
        path.rotate(3);
    };

    view.on('frame', frameHandler);
    ```
*   `on(param)`

    Attach one or more event handlers to the view.

    * Parameters:
    * `param:` `Object` — an object literal containing one or more of the following properties: `frame`, `resize`
    * Returns:
    * `View` — this view itself, so calls can be chained

    Example:Create a rectangle shaped path with its top left point at: {x: 50, y: 25} and a size of {width: 50, height: 50}

    ```jsx
    var path = new Path.Rectangle(new Point(50, 25), new Size(50, 50));
    path.fillColor = 'black';

    var frameHandler = function(event) {
        // Every frame, rotate the path by 3 degrees:
        path.rotate(3);
    };

    view.on({
        frame: frameHandler
    });
    ```
*   `off(type, function)`

    Detach an event handler from the view.

    * Parameters:
    * `type:` `String` — the event type: `‘frame’`, `‘resize’`, `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘click’`, `‘doubleclick’`, `‘mousemove’`, `‘mouseenter’`, `‘mouseleave’`
    * `function:` `Function` — the function to be detached
    * Returns:
    * `View` — this view itself, so calls can be chained

    Example:Create a rectangle shaped path with its top left point at: {x: 50, y: 25} and a size of {width: 50, height: 50}

    ```jsx
    var path = new Path.Rectangle(new Point(50, 25), new Size(50, 50));
    path.fillColor = 'black';

    var frameHandler = function(event) {
        // Every frame, rotate the path by 3 degrees:
        path.rotate(3);
    };

    view.on({
        frame: frameHandler
    });

    // When the user presses the mouse,
    // detach the frame handler from the view:
    function onMouseDown(event) {
        view.off('frame');
    }
    ```
*   `off(param)`

    Detach one or more event handlers from the view.

    * Parameters:
    * `param:` `Object` — an object literal containing one or more of the following properties: `frame`, `resize`
    * Returns:
    * `View` — this view itself, so calls can be chained
*   `emit(type, event)`

    Emit an event on the view.

    * Parameters:
    * `type:` `String` — the event type: `‘frame’`, `‘resize’`, `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘click’`, `‘doubleclick’`, `‘mousemove’`, `‘mouseenter’`, `‘mouseleave’`
    * `event:` `Object` — an object literal containing properties describing the event
    * Returns:
    * `Boolean` — `true` if the event had listeners, `false` otherwise
*   `responds(type)`

    Check if the view has one or more event handlers of the specified type.

    * Parameters:
    * `type:` `String` — the event type: `‘frame’`, `‘resize’`, `‘mousedown’`, `‘mouseup’`, `‘mousedrag’`, `‘click’`, `‘doubleclick’`, `‘mousemove’`, `‘mouseenter’`, `‘mouseleave’`
    * Returns:
    * `Boolean` — `true` if the view has one or more event handlers of the specified type, `false` otherwise
