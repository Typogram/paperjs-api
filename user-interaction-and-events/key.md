# Key

## Static Properties

*   `Key.modifiers`

    The current state of the keyboard modifiers.

    * Type:
    * `Object`
    * Options:
    * `modifiers.shift: Boolean` — `true` if the shift key is pressed, `false` otherwise.
    * `modifiers.control: Boolean` — `true` if the control key is pressed, `false` otherwise.
    * `modifiers.alt: Boolean` — `true` if the alt/option key is pressed, `false` otherwise.
    * `modifiers.meta: Boolean` — `true` if the meta/windows/command key is pressed, `false` otherwise.
    * `modifiers.capsLock: Boolean` — `true` if the caps-lock key is active, `false` otherwise.
    * `modifiers.space: Boolean` — `true` if the space key is pressed, `false` otherwise.
    * `modifiers.option: Boolean` — `true` if the alt/option key is pressed, `false` otherwise. This is the same as `modifiers.alt`
    * `modifiers.command: Boolean` — `true` if the meta key is pressed on Mac, or the control key is pressed on Windows and Linux, `false` otherwise.

## Static Methods

*   `Key.isDown(key)`

    Checks whether the specified key is pressed.

    * Parameters:
    * `key:` `String` — any character or special key descriptor: `‘enter’`, `‘space’`, `‘shift’`, `‘control’`, `‘alt’`, `‘meta’`, `‘caps-lock’`, `‘left’`, `‘up’`, `‘right’`, `‘down’`, `‘escape’`, `‘delete’`, …
    * Returns:
    * `Boolean` — `true` if the key is pressed, `false` otherwise

    Example:Whenever the user clicks, create a circle shaped path. If the 'a' key is pressed, fill it with red, otherwise fill it with blue:

    ```jsx
    function onMouseDown(event) {
        var path = new Path.Circle(event.point, 10);
        if (Key.isDown('a')) {
            path.fillColor = 'red';
        } else {
            path.fillColor = 'blue';
        }
    }
    ```
