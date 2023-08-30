# GradientStop

The GradientStop object.

## Constructors

*   `GradientStop([color[, offset]])`

    Creates a GradientStop object.

    * Parameters:
    * `color:` `Color` — the color of the stop — optional, default: `new Color(0, 0, 0)`
    * `offset:` `Number` — the position of the stop on the gradient ramp as a value between `0` and `1`; `null` or `undefined` for automatic assignment. — optional, default: `null`
    * Returns:
    * `GradientStop`

## Properties

*   `offset`

    The ramp-point of the gradient stop as a value between `0` and `1`.

    * Type:
    * `Number`

    Example:Animating a gradient's ramp points:

    ```jsx
    // Create a circle shaped path at the center of the view,
    // using 40% of the height of the view as its radius
    // and fill it with a radial gradient color:
    var path = new Path.Circle({
        center: view.center,
        radius: view.bounds.height * 0.4
    });

    path.fillColor = {
        gradient: {
            stops: [['yellow', 0.05], ['red', 0.2], ['black', 1]],
            radial: true
        },
        origin: path.position,
        destination: path.bounds.rightCenter
    };

    var gradient = path.fillColor.gradient;

    // This function is called each frame of the animation:
    function onFrame(event) {
        var blackStop = gradient.stops[2];
        // Animate the offset between 0.7 and 0.9:
        blackStop.offset = Math.sin(event.time * 5) * 0.1 + 0.8;

        // Animate the offset between 0.2 and 0.4
        var redStop = gradient.stops[1];
        redStop.offset = Math.sin(event.time * 3) * 0.1 + 0.3;
    }
    ```
*   `color`

    The color of the gradient stop.

    * Type:
    * `Color`

    Example:Animating a gradient's ramp points:

    ```jsx
    // Create a circle shaped path at the center of the view,
    // using 40% of the height of the view as its radius
    // and fill it with a radial gradient color:
    var path = new Path.Circle({
        center: view.center,
        radius: view.bounds.height * 0.4
    });

    path.fillColor = {
        gradient: {
            stops: [['yellow', 0.05], ['red', 0.2], ['black', 1]],
            radial: true
        },
        origin: path.position,
        destination: path.bounds.rightCenter
    };

    var redStop = path.fillColor.gradient.stops[1];
    var blackStop = path.fillColor.gradient.stops[2];

    // This function is called each frame of the animation:
    function onFrame(event) {
        // Animate the offset between 0.7 and 0.9:
        blackStop.offset = Math.sin(event.time * 5) * 0.1 + 0.8;

        // Animate the offset between 0.2 and 0.4
        redStop.offset = Math.sin(event.time * 3) * 0.1 + 0.3;
    }
    ```

## Methods

* `clone()`
  * Returns:
  * `GradientStop` — a copy of the gradient-stop
