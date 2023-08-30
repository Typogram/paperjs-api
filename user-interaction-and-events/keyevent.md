# KeyEvent

Extends **`[Event](Event%20701eceeb8e6f49ec8a30675a8da31f48.md)`**

The KeyEvent object is received by the `Tool`’s keyboard handlers `tool.onKeyDown`, `tool.onKeyUp`. The KeyEvent object is the only parameter passed to these functions and contains information about the keyboard event.

## Properties

*   `type`

    The type of mouse event.

    * Values:
    * `'keydown'`, `'keyup'`
    * Type:
    * `String`
*   `character`

    The character representation of the key that caused this key event, taking into account the current key-modifiers (e.g. shift, control, caps-lock, etc.)

    * Type:
    * `String`
*   `key`

    The key that caused this key event, either as a lower-case character or special key descriptor.

    * Values:
    * `'enter'`, `'space'`, `'shift'`, `'control'`, `'alt'`, `'meta'`, `'caps-lock'`, `'left'`, `'up'`, `'right'`, `'down'`, `'escape'`, `'delete'`, …
    * Type:
    * `String`

## Methods

* `toString()`
  * Returns:
  * `String` — a string representation of the key event

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
