# Gradient

The Gradient object.

Example:Applying a linear gradient color containing evenly distributed color stops:

```jsx
// Define two points which we will be using to construct
// the path and to position the gradient color:
var topLeft = view.center - [80, 80];
var bottomRight = view.center + [80, 80];

// Create a rectangle shaped path between
// the topLeft and bottomRight points:
var path = new Path.Rectangle({
    topLeft: topLeft,
    bottomRight: bottomRight,
    // Fill the path with a gradient of three color stops
    // that runs between the two points we defined earlier:
    fillColor: {
        gradient: {
            stops: ['yellow', 'red', 'blue']
        },
        origin: topLeft,
        destination: bottomRight
    }
});
```

Example:Create a circle shaped path at the center of the view, using 40% of the height of the view as its radius and fill it with a radial gradient color:

```jsx
var path = new Path.Circle({
    center: view.center,
    radius: view.bounds.height * 0.4
});

// Fill the path with a radial gradient color with three stops:
// yellow from 0% to 5%, mix between red from 5% to 20%,
// mix between red and black from 20% to 100%:
path.fillColor = {
    gradient: {
        stops: [['yellow', 0.05], ['red', 0.2], ['black', 1]],
        radial: true
    },
    origin: path.position,
    destination: path.bounds.rightCenter
};
```

## Properties

*   `stops`

    The gradient stops on the gradient ramp.

    * Type:
    * Array of `GradientStop` objects
*   `radial`

    Specifies whether the gradient is radial or linear.

    * Type:
    * `Boolean`

## Methods

* `clone()`
  * Returns:
  * `Gradient` — a copy of the gradient
*   `equals(gradient)`

    Checks whether the gradient is equal to the supplied gradient.

    * Parameters:
    * `gradient:` `Gradient`
    * Returns:
    * `Boolean` — `true` if they are equal, `false` otherwise
