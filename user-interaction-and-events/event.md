# Event

The Event object is the base class for any of the other event types, such as `[MouseEvent](MouseEvent%2089db2df80d0b44ae9a8ffe9f3f4b051c.md)`, `[ToolEvent](ToolEvent%20fb046e93f06f459c81050c846073e385.md)` and `[KeyEvent](KeyEvent%20fea979a99b97464cab44d0ae91000dff.md)`.

## Properties

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

## Methods

*   `preventDefault()`

    Cancels the event if it is cancelable, without stopping further propagation of the event.
*   `stopPropagation()`

    Prevents further propagation of the current event.
*   `stop()`

    Cancels the event if it is cancelable, and stops stopping further propagation of the event. This is has the same effect as calling both `stopPropagation`() and `preventDefault`().

    Any handler can also return `false` to indicate that `stop()` should be called right after.
