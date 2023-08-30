# MouseEvent

Extends **`[Event](Event%20701eceeb8e6f49ec8a30675a8da31f48.md)`**

The MouseEvent object is received by the `[Item](Item%20eab4980134ff44238bc91e6d4a28d6f9.md)`’s mouse event handlers `item.onMouseDown`, `item.onMouseDrag`, `item.onMouseMove`, `item.onMouseUp`, `item.onClick`, `item.onDoubleClick`, `item.onMouseEnter` and `item.onMouseLeave`. The MouseEvent object is the only parameter passed to these functions and contains information about the mouse event.

## Properties

*   `type`

    The type of mouse event.

    * Values:
      * `'mousedown'`, `'mouseup'`, `'mousedrag'`, `'click'`, `'doubleclick'`, `'mousemove'`, `'mouseenter'`, `'mouseleave'`
    * Type:
      * `String`
*   `point`

    The position of the mouse in project coordinates when the event was fired.

    * Type:
      * `Point`
*   `target`

    The item that dispatched the event. It is different from `currentTarget` when the event handler is called during the bubbling phase of the event.

    * Type:
      * `Item`
*   `currentTarget`

    The current target for the event, as the event traverses the scene graph. It always refers to the element the event handler has been attached to as opposed to `target` which identifies the element on which the event occurred.

    * Type:
      * `Item`
* `delta`
  * Type:
    * `Point`

## Methods

* `toString()`
  * Returns:
  * `String` — a string representation of the mouse event

## Properties inherited from `Event`

*   `timeStamp`

    The time at which the event was created, in milliseconds since the epoch.

    Read only.

    * Type:
      * `Number`
*   `modifiers`

    The current state of the keyboard modifiers.

    Read only.

    * Type:
      * `object`
    * See also:
      * `Key.modifiers`

## Methods inherited from `Event`

*   `preventDefault()`

    Cancels the event if it is cancelable, without stopping further propagation of the event.
*   `stopPropagation()`

    Prevents further propagation of the current event.
*   `stop()`

    Cancels the event if it is cancelable, and stops stopping further propagation of the event. This is has the same effect as calling both `stopPropagation`() and `preventDefault`().

    Any handler can also return `false` to indicate that `stop()` should be called right after.
