# Color

All properties and functions that expect color values in the form of instances of Color objects, also accept named colors and hex values as strings which are then converted to instances of `Color` internally.

Example: Named color values:

```jsx
// Create a circle shaped path at {x: 80, y: 50}
// with a radius of 30.
var circle = new Path.Circle(new Point(80, 50), 30);

// Pass a color name to the fillColor property, which is internally
// converted to a Color.
circle.fillColor = 'green';
```

Example: Hex color values:

```jsx
// Create a circle shaped path at {x: 80, y: 50}
// with a radius of 30.
var circle = new Path.Circle(new Point(80, 50), 30);

// Pass a hex string to the fillColor property, which is internally
// converted to a Color.
circle.fillColor = '#ff0000';
```

## Constructors

*   `Color(red, green, blue[, alpha])`

    Creates a RGB Color object.

    * Parameters:
    * `red:` `Number` — the amount of red in the color as a value between `0` and `1`
    * `green:` `Number` — the amount of green in the color as a value between `0` and `1`
    * `blue:` `Number` — the amount of blue in the color as a value between `0` and `1`
    * `alpha:` `Number` — the alpha of the color as a value between `0` and `1` — optional
    * Returns:
    * `Color`

    Example:Creating a RGB Color:

    ```jsx
    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 30:
    var circle = new Path.Circle(new Point(80, 50), 30);

    // 100% red, 0% blue, 50% blue:
    circle.fillColor = new Color(1, 0, 0.5);
    ```
*   `Color(gray[, alpha])`

    Creates a gray Color object.

    * Parameters:
    * `gray:` `Number` — the amount of gray in the color as a value between `0` and `1`
    * `alpha:` `Number` — the alpha of the color as a value between `0` and `1` — optional
    * Returns:
    * `Color`

    Example:Creating a gray Color:

    ```jsx
    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 30:
    var circle = new Path.Circle(new Point(80, 50), 30);

    // Create a GrayColor with 50% gray:
    circle.fillColor = new Color(0.5);
    ```
*   `Color(object)`

    Creates a HSB, HSL or gradient Color object from the properties of the provided object:

    * Options:
    * `hsb.hue: Number` — the hue of the color as a value in degrees between `0` and `360`
    * `hsb.saturation: Number` — the saturation of the color as a value between `0` and `1`
    * `hsb.brightness: Number` — the brightness of the color as a value between `0` and `1`
    * `hsb.alpha: Number` — the alpha of the color as a value between `0` and `1`
    * `hsl.hue: Number` — the hue of the color as a value in degrees between `0` and `360`
    * `hsl.saturation: Number` — the saturation of the color as a value between `0` and `1`
    * `hsl.lightness: Number` — the lightness of the color as a value between `0` and `1`
    * `hsl.alpha: Number` — the alpha of the color as a value between `0` and `1`
    * `gradient.gradient: Gradient` — the gradient object that describes the color stops and type of gradient to be used
    * `gradient.origin: Point` — the origin point of the gradient
    * `gradient.destination: Point` — the destination point of the gradient
    * `gradient.stops: Array of GradientStop` objects — the gradient stops describing the gradient, as an alternative to providing a gradient object
    * `gradient.radial: Boolean` — controls whether the gradient is radial, as an alternative to providing a gradient object
    * Parameters:
    * `object:` `Object` — an object describing the components and properties of the color
    * Returns:
    * `Color`

    Example:Creating a HSB Color:

    ```jsx
    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 30:
    var circle = new Path.Circle(new Point(80, 50), 30);

    // Create an HSB Color with a hue of 90 degrees, a saturation
    // 100% and a brightness of 100%:
    circle.fillColor = { hue: 90, saturation: 1, brightness: 1 };
    ```

    Example:Creating a HSL Color:

    ```jsx
    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 30:
    var circle = new Path.Circle(new Point(80, 50), 30);

    // Create an HSL Color with a hue of 90 degrees, a saturation
    // 100% and a lightness of 50%:
    circle.fillColor = { hue: 90, saturation: 1, lightness: 0.5 };
    ```

    Example:Creating a gradient color from an object literal:

    ```jsx
    // Define two points which we will be using to construct
    // the path and to position the gradient color:
    var topLeft = view.center - [80, 80];
    var bottomRight = view.center + [80, 80];

    var path = new Path.Rectangle({
     topLeft: topLeft,
     bottomRight: bottomRight,
     // Fill the path with a gradient of three color stops
     // that runs between the two points we defined earlier:
     fillColor: {
         stops: ['yellow', 'red', 'blue'],
         origin: topLeft,
         destination: bottomRight
     }
    });
    ```
*   `Color(color)`

    Creates a Color object from a CSS string. All common CSS color string formats are supported: - Named colors (e.g. `'red'`, `'fuchsia'`, …) - Hex strings (`'#ffff00'`, `'#ff0'`, …) - RGB strings (`'rgb(255, 128, 0)'`, `'rgba(255, 128, 0, 0.5)'`, …) - HSL strings (`'hsl(180deg, 20%, 50%)'`, `'hsla(3.14rad, 20%, 50%, 0.5)'`, …)

    * Parameters:
    * `color:` `String` — the color’s CSS string representation
    * Returns:
    * `Color`

    Example:

    ```jsx
    var circle = new Path.Circle({
        center: [80, 50],
        radius: 30,
        fillColor: new Color('rgba(255, 255, 0, 0.5)')
    });
    ```
*   `Color(gradient, origin, destination[, highlight])`

    Creates a gradient Color object.

    * Parameters:
    * `gradient:` `Gradient`
    * `origin:` `Point`
    * `destination:` `Point`
    * `highlight:` `Point` — optional
    * Returns:
    * `Color`

    Example:Applying a linear gradient color containing evenly distributed color stops:

    ```jsx
    // Define two points which we will be using to construct
    // the path and to position the gradient color:
    var topLeft = view.center - [80, 80];
    var bottomRight = view.center + [80, 80];

    // Create a rectangle shaped path between
    // the topLeft and bottomRight points:
    var path = new Path.Rectangle(topLeft, bottomRight);

    // Create the gradient, passing it an array of colors to be converted
    // to evenly distributed color stops:
    var gradient = new Gradient(['yellow', 'red', 'blue']);

    // Have the gradient color run between the topLeft and
    // bottomRight points we defined earlier:
    var gradientColor = new Color(gradient, topLeft, bottomRight);

    // Set the fill color of the path to the gradient color:
    path.fillColor = gradientColor;
    ```

    Example:Applying a radial gradient color containing unevenly distributed color stops:

    ```jsx
    // Create a circle shaped path at the center of the view
    // with a radius of 80:
    var path = new Path.Circle({
        center: view.center,
        radius: 80
    });

    // The stops array: yellow mixes with red between 0 and 15%,
    // 15% to 30% is pure red, red mixes with black between 30% to 100%:
    var stops = [
        ['yellow', 0],
        ['red', 0.15],
        ['red', 0.3],
        ['black', 0.9]
    ];

    // Create a radial gradient using the color stops array:
    var gradient = new Gradient(stops, true);

    // We will use the center point of the circle shaped path as
    // the origin point for our gradient color
    var from = path.position;

    // The destination point of the gradient color will be the
    // center point of the path + 80pt in horizontal direction:
    var to = path.position + [80, 0];

    // Create the gradient color:
    var gradientColor = new Color(gradient, from, to);

    // Set the fill color of the path to the gradient color:
    path.fillColor = gradientColor;
    ```

## Operators

*   `+number`, `+color`

    Returns the addition of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to add
    * Returns:
    * `Color` — the addition of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color + 1;
    console.log(result); // { red: 1, blue: 1, green: 1 }
    ```

    Returns the addition of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to add
    * Returns:
    * `Color` — the addition of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(1, 0, 0);
    var result = color1 + color2;
    console.log(result); // { red: 1, blue: 1, green: 1 }
    ```
*   `-number`, `-color`

    Returns the subtraction of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to subtract
    * Returns:
    * `Color` — the subtraction of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color - 1;
    console.log(result); // { red: 0, blue: 0, green: 0 }
    ```

    Returns the subtraction of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to subtract
    * Returns:
    * `Color` — the subtraction of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(1, 0, 0);
    var result = color1 - color2;
    console.log(result); // { red: 0, blue: 1, green: 1 }
    ```
*   `*number`, `*color`

    Returns the multiplication of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to multiply
    * Returns:
    * `Color` — the multiplication of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color * 0.5;
    console.log(result); // { red: 0.25, blue: 0.5, green: 0.5 }
    ```

    Returns the multiplication of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to multiply
    * Returns:
    * `Color` — the multiplication of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(0.5, 0, 0.5);
    var result = color1 * color2;
    console.log(result); // { red: 0, blue: 0, green: 0.5 }
    ```
*   `/number`, `/color`

    Returns the division of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to divide
    * Returns:
    * `Color` — the division of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color / 2;
    console.log(result); // { red: 0.25, blue: 0.5, green: 0.5 }
    ```

    Returns the division of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to divide
    * Returns:
    * `Color` — the division of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(0.5, 0, 0.5);
    var result = color1 / color2;
    console.log(result); // { red: 0, blue: 0, green: 1 }
    ```

## Properties

*   `type`

    The type of the color as a string.

    * Type:
    * `String`

    Example:

    ```jsx
    var color = new Color(1, 0, 0);
    console.log(color.type); // 'rgb'
    ```
*   `components`

    The color components that define the color, including the alpha value if defined.

    Read only.

    * Type:
    * Array of `Numbers`
*   `alpha`

    The color’s alpha value as a number between `0` and `1`. All colors of the different subclasses support alpha values.

    * Default:
    * `1`
    * Type:
    * `Number`

    Example: A filled path with a half transparent stroke:

    ```jsx
    var circle = new Path.Circle(new Point(80, 50), 30);

    // Fill the circle with red and give it a 20pt green stroke:
    circle.style = {
     fillColor: 'red',
     strokeColor: 'green',
     strokeWidth: 20
    };

    // Make the stroke half transparent:
    circle.strokeColor.alpha = 0.5;
    ```

### RGB Components

*   `red`

    The amount of red in the color as a value between `0` and `1`.

    * Type:
    * `Number`

    Example: Changing the amount of red in a color:

    ```jsx
    var circle = new Path.Circle(new Point(80, 50), 30);
    circle.fillColor = 'blue';

    // Blue + red = purple:
    circle.fillColor.red = 1;
    ```
*   `green`

    The amount of green in the color as a value between `0` and `1`.

    * Type:
    * `Number`

    Example: Changing the amount of green in a color:

    ```jsx
    var circle = new Path.Circle(new Point(80, 50), 30);

    // First we set the fill color to red:
    circle.fillColor = 'red';

    // Red + green = yellow:
    circle.fillColor.green = 1;
    ```
*   `blue`

    The amount of blue in the color as a value between `0` and `1`.

    * Type:
    * `Number`

    Example: Changing the amount of blue in a color:

    ```jsx
    var circle = new Path.Circle(new Point(80, 50), 30);

    // First we set the fill color to red:
    circle.fillColor = 'red';

    // Red + blue = purple:
    circle.fillColor.blue = 1;
    ```

### Gray Components

*   `gray`

    The amount of gray in the color as a value between `0` and `1`.

    * Type:
    * `Number`

### HSB Components

*   `hue`

    The hue of the color as a value in degrees between `0` and `360`.

    * Type:
    * `Number`

    Example: Changing the hue of a color:

    ```jsx
    var circle = new Path.Circle(new Point(80, 50), 30);
    circle.fillColor = 'red';
    circle.fillColor.hue += 30;
    ```

    Example: Hue cycling:

    ```jsx
    // Create a rectangle shaped path, using the dimensions
    // of the view:
    var path = new Path.Rectangle(view.bounds);
    path.fillColor = 'red';

    function onFrame(event) {
     path.fillColor.hue += 0.5;
    }
    ```
*   `saturation`

    The saturation of the color as a value between `0` and `1`.

    * Type:
    * `Number`
*   `brightness`

    The brightness of the color as a value between `0` and `1`.

    * Type:
    * `Number`

### HSL Components

*   `lightness`

    The lightness of the color as a value between `0` and `1`.

    Note that all other components are shared with HSB.

    * Type:
    * `Number`

### Gradient Components

*   `gradient`

    The gradient object describing the type of gradient and the stops.

    * Type:
    * `Gradient`
*   `highlight`

    The highlight point of the gradient.

    * Type:
    * `Point`

    Example: Create a circle shaped path at the center of the view, using 40% of the height of the view as its radius and fill it with a radial gradient color:

    ```jsx
    var path = new Path.Circle({
     center: view.center,
     radius: view.bounds.height * 0.4
    });

    path.fillColor = {
     gradient: {
         stops: ['yellow', 'red', 'black'],
         radial: true
     },
     origin: path.position,
     destination: path.bounds.rightCenter
    };

    function onMouseMove(event) {
     // Set the origin highlight of the path's gradient color
     // to the position of the mouse:
     path.fillColor.highlight = event.point;
    }
    ```

## Methods

*   `set(...values)`

    Sets the color to the passed values. Note that any sequence of parameters that is supported by the various `Color`() constructors also work for calls of `set()`.

    * Parameters:
    * `values:` `any value`
    * Returns:
    * `Color`
*   `convert(type)`

    Converts the color to another type.

    * Parameters:
    * `type:` `String` — the color type to convert to. Possible values: `‘rgb’`, `‘gray’`, `‘hsb’`, `‘hsl’`
    * Returns:
    * `Color` — the converted color as a new instance
*   `hasAlpha()`

    Checks if the color has an alpha value.

    * Returns:
    * `Boolean` — `true` if the color has an alpha value, `false` otherwise
*   `equals(color)`

    Checks if the component color values of the color are the same as those of the supplied one.

    * Parameters:
    * `color:` `Color` — the color to compare with
    * Returns:
    * `Boolean` — `true` if the colors are the same, `false` otherwise
* `clone()`
  * Returns:
  * `Color` — a copy of the color object

### String Representations

* `toString()`
  * Returns:
  * `String` — a string representation of the color
*   `toCSS(hex)`

    Returns the color as a CSS string.

    * Parameters:
    * `hex:` `Boolean` — whether to return the color in hexadecimal representation or as a CSS RGB / RGBA string.
    * Returns:
    * `String` — a CSS string representation of the color
*   `transform(matrix)`

    Transform the gradient color by the specified matrix.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to transform the gradient color by

### Math Operator Functions

*   `add(number)`

    Returns the addition of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to add
    * Returns:
    * `Color` — the addition of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color + 1;
    console.log(result); // { red: 1, blue: 1, green: 1 }
    ```
*   `add(color)`

    Returns the addition of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to add
    * Returns:
    * `Color` — the addition of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(1, 0, 0);
    var result = color1 + color2;
    console.log(result); // { red: 1, blue: 1, green: 1 }
    ```
*   `subtract(number)`

    Returns the subtraction of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to subtract
    * Returns:
    * `Color` — the subtraction of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color - 1;
    console.log(result); // { red: 0, blue: 0, green: 0 }
    ```
*   `subtract(color)`

    Returns the subtraction of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to subtract
    * Returns:
    * `Color` — the subtraction of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(1, 0, 0);
    var result = color1 - color2;
    console.log(result); // { red: 0, blue: 1, green: 1 }
    ```
*   `multiply(number)`

    Returns the multiplication of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to multiply
    * Returns:
    * `Color` — the multiplication of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color * 0.5;
    console.log(result); // { red: 0.25, blue: 0.5, green: 0.5 }
    ```
*   `multiply(color)`

    Returns the multiplication of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to multiply
    * Returns:
    * `Color` — the multiplication of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(0.5, 0, 0.5);
    var result = color1 * color2;
    console.log(result); // { red: 0, blue: 0, green: 0.5 }
    ```
*   `divide(number)`

    Returns the division of the supplied value to both coordinates of the color as a new color. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to divide
    * Returns:
    * `Color` — the division of the color and the value as a new color

    Example:

    ```jsx
    var color = new Color(0.5, 1, 1);
    var result = color / 2;
    console.log(result); // { red: 0.25, blue: 0.5, green: 0.5 }
    ```
*   `divide(color)`

    Returns the division of the supplied color to the color as a new color. The object itself is not modified!

    * Parameters:
    * `color:` `Color` — the color to divide
    * Returns:
    * `Color` — the division of the two colors as a new color

    Example:

    ```jsx
    var color1 = new Color(0, 1, 1);
    var color2 = new Color(0.5, 0, 0.5);
    var result = color1 / color2;
    console.log(result); // { red: 0, blue: 0, green: 1 }
    ```

## Static Methods

*   `Color.random()`

    Returns a color object with random `red`, `green` and `blue` values between `0` and `1`.

    * Returns:
    * `Color` — the newly created color object

    Example:

    ```jsx
    var circle = new Path.Circle(view.center, 50);
    // Set a random color as circle fill color.
    circle.fillColor = Color.random();
    ```
