# Rectangle

A Rectangle specifies an area that is enclosed by it’s top-left point (x, y), its width, and its height. It should not be confused with a rectangular path, it is not an item.

## Constructors

*   `Rectangle(point, size)`

    Creates a Rectangle object.

    * Parameters:
    * `point:` `Point` — the top-left point of the rectangle
    * `size:` `Size` — the size of the rectangle
    * Returns:
    * `Rectangle`
*   `Rectangle(object)`

    Creates a Rectangle object.

    * Parameters:
    * `object:` `Object` — an object containing properties to be set on the rectangle
    * Returns:
    * `Rectangle`

    Example:Create a rectangle between {x: 20, y: 20} and {x: 80, y:80}

    ```jsx
    var rectangle = new Rectangle({
        point: [20, 20],
        size: [60, 60]
    });
    ```

    Example:Create a rectangle between {x: 20, y: 20} and {x: 80, y:80}

    ```jsx
    var rectangle = new Rectangle({
        from: [20, 20],
        to: [80, 80]
    });
    ```
*   `Rectangle(x, y, width, height)`

    Creates a rectangle object.

    * Parameters:
    * `x:` `Number` — the left coordinate
    * `y:` `Number` — the top coordinate
    * `width:` `Number`
    * `height:` `Number`
    * Returns:
    * `Rectangle`
*   `Rectangle(from, to)`

    Creates a rectangle object from the passed points. These do not necessarily need to be the top left and bottom right corners, the constructor figures out how to fit a rectangle between them.

    * Parameters:
    * `from:` `Point` — the first point defining the rectangle
    * `to:` `Point` — the second point defining the rectangle
    * Returns:
    * `Rectangle`
*   `Rectangle(rectangle)`

    Creates a new rectangle object from the passed rectangle object.

    * Parameters:
    * `rectangle:` `Rectangle`
    * Returns:
    * `Rectangle`

## Properties

*   `x`

    The x position of the rectangle.

    * Type:
    * `Number`
*   `y`

    The y position of the rectangle.

    * Type:
    * `Number`
*   `width`

    The width of the rectangle.

    * Type:
    * `Number`
*   `height`

    The height of the rectangle.

    * Type:
    * `Number`
*   `point`

    The top-left point of the rectangle

    * Type:
    * `Point`
*   `size`

    The size of the rectangle

    * Type:
    * `Size`

### Side Positions

*   `left`

    The position of the left hand side of the rectangle. Note that this doesn’t move the whole rectangle; the right hand side stays where it was.

    * Type:
    * `Number`
*   `top`

    The top coordinate of the rectangle. Note that this doesn’t move the whole rectangle: the bottom won’t move.

    * Type:
    * `Number`
*   `right`

    The position of the right hand side of the rectangle. Note that this doesn’t move the whole rectangle; the left hand side stays where it was.

    * Type:
    * `Number`
*   `bottom`

    The bottom coordinate of the rectangle. Note that this doesn’t move the whole rectangle: the top won’t move.

    * Type:
    * `Number`

### Corner and Center Point Positions

*   `center`

    The center point of the rectangle.

    * Type:
    * `Point`
*   `topLeft`

    The top-left point of the rectangle.

    * Type:
    * `Point`
*   `topRight`

    The top-right point of the rectangle.

    * Type:
    * `Point`
*   `bottomLeft`

    The bottom-left point of the rectangle.

    * Type:
    * `Point`
*   `bottomRight`

    The bottom-right point of the rectangle.

    * Type:
    * `Point`
*   `leftCenter`

    The left-center point of the rectangle.

    * Type:
    * `Point`
*   `topCenter`

    The top-center point of the rectangle.

    * Type:
    * `Point`
*   `rightCenter`

    The right-center point of the rectangle.

    * Type:
    * `Point`
*   `bottomCenter`

    The bottom-center point of the rectangle.

    * Type:
    * `Point`
*   `area`

    The area of the rectangle.

    Read only.

    * Type:
    * `Number`

### Item Bounds

*   `selected`

    Specifies whether an item’s bounds are to appear as selected.

    Paper.js draws the bounds of items with selected bounds on top of your project. This is very useful when debugging.

    * Default:
    * `false`
    * Type:
    * `Boolean`

    Example:

    Run

    ```jsx
    var path = new Path.Circle({
        center: [80, 50],
        radius: 40,
        selected: true
    });

    path.bounds.selected = true;
    ```

## Methods

*   `set(...values)`

    Sets the rectangle to the passed values. Note that any sequence of parameters that is supported by the various `Rectangle`() constructors also work for calls of `set()`.

    * Parameters:
    * `values:` `any value`
    * Returns:
    * `Rectangle`
*   `clone()`

    Returns a copy of the rectangle.

    * Returns:
    * `Rectangle`
*   `equals(rect)`

    Checks whether the coordinates and size of the rectangle are equal to that of the supplied rectangle.

    * Parameters:
    * `rect:` `Rectangle`
    * Returns:
    * `Boolean` — `true` if the rectangles are equal, `false` otherwise
* `toString()`
  * Returns:
  * `String` — a string representation of this rectangle
* `isEmpty()`
  * Returns:
  * `Boolean` — `true` if the rectangle is empty, `false` otherwise

### Geometric Tests

*   `contains(point)`

    Tests if the specified point is inside the boundary of the rectangle.

    * Parameters:
    * `point:` `Point` — the specified point
    * Returns:
    * `Boolean` — `true` if the point is inside the rectangle’s boundary, `false` otherwise

    Example:Checking whether the mouse position falls within the bounding rectangle of an item:

    Run

    ```jsx
    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 30.
    var circle = new Path.Circle(new Point(80, 50), 30);
    circle.fillColor = 'red';

    function onMouseMove(event) {
        // Check whether the mouse position intersects with the
        // bounding box of the item:
        if (circle.bounds.contains(event.point)) {
            // If it intersects, fill it with green:
            circle.fillColor = 'green';
        } else {
            // If it doesn't intersect, fill it with red:
            circle.fillColor = 'red';
        }
    }
    ```
*   `contains(rect)`

    Tests if the interior of the rectangle entirely contains the specified rectangle.

    * Parameters:
    * `rect:` `Rectangle` — the specified rectangle
    * Returns:
    * `Boolean` — `true` if the rectangle entirely contains the specified rectangle, `false` otherwise

    Example:Checking whether the bounding box of one item is contained within that of another item:

    Run

    ```jsx
    // All newly created paths will inherit these styles:
    project.currentStyle = {
        fillColor: 'green',
        strokeColor: 'black'
    };

    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 45.
    var largeCircle = new Path.Circle(new Point(80, 50), 45);

    // Create a smaller circle shaped path in the same position
    // with a radius of 30.
    var circle = new Path.Circle(new Point(80, 50), 30);

    function onMouseMove(event) {
        // Move the circle to the position of the mouse:
        circle.position = event.point;

        // Check whether the bounding box of the smaller circle
        // is contained within the bounding box of the larger item:
        if (largeCircle.bounds.contains(circle.bounds)) {
            // If it does, fill it with green:
            circle.fillColor = 'green';
            largeCircle.fillColor = 'green';
        } else {
            // If doesn't, fill it with red:
            circle.fillColor = 'red';
            largeCircle.fillColor = 'red';
        }
    }
    ```
*   `intersects(rect[, epsilon])`

    Tests if the interior of this rectangle intersects the interior of another rectangle. Rectangles just touching each other are considered as non-intersecting, except if a `epsilon` value is specified by which this rectangle’s dimensions are increased before comparing.

    * Parameters:
    * `rect:` `Rectangle` — the specified rectangle
    * `epsilon:` `Number` — the epsilon against which to compare the rectangle’s dimensions — optional, default: `0`
    * Returns:
    * `Boolean` — `true` if the rectangle and the specified rectangle intersect each other, `false` otherwise

    Example:Checking whether the bounding box of one item intersects with that of another item:

    Run

    ```jsx
    // All newly created paths will inherit these styles:
    project.currentStyle = {
        fillColor: 'green',
        strokeColor: 'black'
    };

    // Create a circle shaped path at {x: 80, y: 50}
    // with a radius of 45.
    var largeCircle = new Path.Circle(new Point(80, 50), 45);

    // Create a smaller circle shaped path in the same position
    // with a radius of 30.
    var circle = new Path.Circle(new Point(80, 50), 30);

    function onMouseMove(event) {
        // Move the circle to the position of the mouse:
        circle.position = event.point;

        // Check whether the bounding box of the two circle
        // shaped paths intersect:
        if (largeCircle.bounds.intersects(circle.bounds)) {
            // If it does, fill it with green:
            circle.fillColor = 'green';
            largeCircle.fillColor = 'green';
        } else {
            // If doesn't, fill it with red:
            circle.fillColor = 'red';
            largeCircle.fillColor = 'red';
        }
    }
    ```

### Boolean Operations

*   `intersect(rect)`

    Returns a new rectangle representing the intersection of this rectangle with the specified rectangle.

    * Parameters:
    * `rect:` `Rectangle` — the rectangle to be intersected with this rectangle
    * Returns:
    * `Rectangle` — the largest rectangle contained in both the specified rectangle and in this rectangle

    Example:Intersecting two rectangles and visualizing the result using rectangle shaped paths:

    Run

    ```jsx
    // Create two rectangles that overlap each other
    var size = new Size(50, 50);
    var rectangle1 = new Rectangle(new Point(25, 15), size);
    var rectangle2 = new Rectangle(new Point(50, 40), size);

    // The rectangle that represents the intersection of the
    // two rectangles:
    var intersected = rectangle1.intersect(rectangle2);

    // To visualize the intersecting of the rectangles, we will
    // create rectangle shaped paths using the Path.Rectangle
    // constructor.

    // Have all newly created paths inherit a black stroke:
    project.currentStyle.strokeColor = 'black';

    // Create two rectangle shaped paths using the abstract rectangles
    // we created before:
    new Path.Rectangle(rectangle1);
    new Path.Rectangle(rectangle2);

    // Create a path that represents the intersected rectangle,
    // and fill it with red:
    var intersectionPath = new Path.Rectangle(intersected);
    intersectionPath.fillColor = 'red';
    ```
*   `unite(rect)`

    Returns a new rectangle representing the union of this rectangle with the specified rectangle.

    * Parameters:
    * `rect:` `Rectangle` — the rectangle to be combined with this rectangle
    * Returns:
    * `Rectangle` — the smallest rectangle containing both the specified rectangle and this rectangle
*   `include(point)`

    Adds a point to this rectangle. The resulting rectangle is the smallest rectangle that contains both the original rectangle and the specified point.

    After adding a point, a call to `contains(point)` with the added point as an argument does not necessarily return `true`. The `rectangle.contains(point)` method does not return `true` for points on the right or bottom edges of a rectangle. Therefore, if the added point falls on the left or bottom edge of the enlarged rectangle, `rectangle.contains(point)` returns `false` for that point.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Rectangle` — the smallest rectangle that contains both the original rectangle and the specified point
*   `expand(amount)`

    Returns a new rectangle expanded by the specified amount in horizontal and vertical directions.

    * Parameters:
    * `amount:` `Number`⟋`Size`⟋`Point` — the amount to expand the rectangle in both directions
    * Returns:
    * `Rectangle` — the expanded rectangle
*   `expand(hor, ver)`

    Returns a new rectangle expanded by the specified amounts in horizontal and vertical directions.

    * Parameters:
    * `hor:` `Number` — the amount to expand the rectangle in horizontal direction
    * `ver:` `Number` — the amount to expand the rectangle in vertical direction
    * Returns:
    * `Rectangle` — the expanded rectangle
*   `scale(amount)`

    Returns a new rectangle scaled by the specified amount from its center.

    * Parameters:
    * `amount:` `Number`
    * Returns:
    * `Rectangle` — the scaled rectangle
*   `scale(hor, ver)`

    Returns a new rectangle scaled in horizontal direction by the specified `hor` amount and in vertical direction by the specified `ver` amount from its center.

    * Parameters:
    * `hor:` `Number`
    * `ver:` `Number`
    * Returns:
    * `Rectangle` — the scaled rectangle
