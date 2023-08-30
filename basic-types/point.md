# Point

The Point object represents a point in the two dimensional space of the Paper.js project. It is also used to represent two dimensional vector objects.

Example:Create a point at x: 10, y: 5

```jsx
var point = new Point(10, 5);
console.log(point.x); // 10
console.log(point.y); // 5
```

## Constructors

*   `Point(x, y)`

    Creates a Point object with the given x and y coordinates.

    * Parameters:
    * `x:` `Number` — the x coordinate
    * `y:` `Number` — the y coordinate
    * Returns:
    * `Point`

    Example:Create a point at x: 10, y: 5

    ```jsx
    var point = new Point(10, 5);
    console.log(point.x); // 10
    console.log(point.y); // 5
    ```
*   `Point(array)`

    Creates a Point object using the numbers in the given array as coordinates.

    * Parameters:
    * `array:` `Array`
    * Returns:
    * `Point`

    Example:Creating a point at x: 10, y: 5 using an array of numbers:

    ```jsx
    var array = [10, 5];
    var point = new Point(array);
    console.log(point.x); // 10
    console.log(point.y); // 5
    ```

    Example:Passing an array to a functionality that expects a point:

    ```jsx
    // Create a circle shaped path at x: 50, y: 50
    // with a radius of 30:
    var path = new Path.Circle([50, 50], 30);
    path.fillColor = 'red';

    // Which is the same as doing:
    var path = new Path.Circle(new Point(50, 50), 30);
    path.fillColor = 'red';
    ```
*   `Point(object)`

    Creates a Point object using the properties in the given object.

    * Parameters:
    * `object:` `Object` — the object describing the point’s properties
    * Returns:
    * `Point`

    Example:Creating a point using an object literal with length and angle properties:

    ```jsx
    var point = new Point({
        length: 10,
        angle: 90
    });
    console.log(point.length); // 10
    console.log(point.angle); // 90
    ```

    Example:Creating a point at x: 10, y: 20 using an object literal:

    ```jsx
    var point = new Point({
        x: 10,
        y: 20
    });
    console.log(point.x); // 10
    console.log(point.y); // 20
    ```

    Example:Passing an object to a functionality that expects a point:

    ```jsx
    var center = {
        x: 50,
        y: 50
    };

    // Creates a circle shaped path at x: 50, y: 50
    // with a radius of 30:
    var path = new Path.Circle(center, 30);
    path.fillColor = 'red';
    ```
*   `Point(size)`

    Creates a Point object using the width and height values of the given Size object.

    * Parameters:
    * `size:` `Size`
    * Returns:
    * `Point`

    Example:Creating a point using a size object.

    ```jsx
    // Create a Size with a width of 100pt and a height of 50pt
    var size = new Size(100, 50);
    console.log(size); // { width: 100, height: 50 }
    var point = new Point(size);
    console.log(point); // { x: 100, y: 50 }
    ```
*   `Point(point)`

    Creates a Point object using the coordinates of the given Point object.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Point`

## Operators

*   `+number`, `+point`

    Returns the addition of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to add
    * Returns:
    * `Point` — the addition of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(5, 10);
    var result = point + 20;
    console.log(result); // {x: 25, y: 30}
    ```

    Returns the addition of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to add
    * Returns:
    * `Point` — the addition of the two points as a new point

    Example:

    ```jsx
    var point1 = new Point(5, 10);
    var point2 = new Point(10, 20);
    var result = point1 + point2;
    console.log(result); // {x: 15, y: 30}
    ```
*   `-number`, `-point`

    Returns the subtraction of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to subtract
    * Returns:
    * `Point` — the subtraction of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(10, 20);
    var result = point - 5;
    console.log(result); // {x: 5, y: 15}
    ```

    Returns the subtraction of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to subtract
    * Returns:
    * `Point` — the subtraction of the two points as a new point

    Example:

    ```jsx
    var firstPoint = new Point(10, 20);
    var secondPoint = new Point(5, 5);
    var result = firstPoint - secondPoint;
    console.log(result); // {x: 5, y: 15}
    ```
*   `*number`, `*point`

    Returns the multiplication of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to multiply by
    * Returns:
    * `Point` — the multiplication of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(10, 20);
    var result = point * 2;
    console.log(result); // {x: 20, y: 40}
    ```

    Returns the multiplication of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to multiply by
    * Returns:
    * `Point` — the multiplication of the two points as a new point

    Example:

    ```jsx
    var firstPoint = new Point(5, 10);
    var secondPoint = new Point(4, 2);
    var result = firstPoint * secondPoint;
    console.log(result); // {x: 20, y: 20}
    ```
*   `/number`, `/point`

    Returns the division of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to divide by
    * Returns:
    * `Point` — the division of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(10, 20);
    var result = point / 2;
    console.log(result); // {x: 5, y: 10}
    ```

    Returns the division of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to divide by
    * Returns:
    * `Point` — the division of the two points as a new point

    Example:

    ```jsx
    var firstPoint = new Point(8, 10);
    var secondPoint = new Point(2, 5);
    var result = firstPoint / secondPoint;
    console.log(result); // {x: 4, y: 2}
    ```
*   `%number`, `%point`

    The modulo operator returns the integer remainders of dividing the point by the supplied value as a new point.

    * Parameters:
    * `value:` `Number`
    * Returns:
    * `Point` — the integer remainders of dividing the point by the value as a new point

    Example:

    ```jsx
    var point = new Point(12, 6);
    console.log(point % 5); // {x: 2, y: 1}
    ```

    The modulo operator returns the integer remainders of dividing the point by the supplied value as a new point.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Point` — the integer remainders of dividing the points by each other as a new point

    Example:

    ```jsx
    var point = new Point(12, 6);
    console.log(point % new Point(5, 2)); // {x: 2, y: 0}
    ```

## Properties

*   `x`

    The x coordinate of the point

    * Type:
    * `Number`
*   `y`

    The y coordinate of the point

    * Type:
    * `Number`
*   `length`

    The length of the vector that is represented by this point’s coordinates. Each point can be interpreted as a vector that points from the origin (`x = 0`, `y = 0`) to the point’s location. Setting the length changes the location but keeps the vector’s angle.

    * Type:
    * `Number`
*   `angle`

    The vector’s angle in degrees, measured from the x-axis to the vector.

    * Type:
    * `Number`
*   `angleInRadians`

    The vector’s angle in radians, measured from the x-axis to the vector.

    * Type:
    * `Number`
*   `quadrant`

    The quadrant of the `angle` of the point.

    Angles between 0 and 90 degrees are in quadrant `1`. Angles between 90 and 180 degrees are in quadrant `2`, angles between 180 and 270 degrees are in quadrant `3` and angles between 270 and 360 degrees are in quadrant `4`.

    Read only.

    * Type:
    * `Number`

    Example:

    ```jsx
    var point = new Point({
        angle: 10,
        length: 20
    });
    console.log(point.quadrant); // 1

    point.angle = 100;
    console.log(point.quadrant); // 2

    point.angle = 190;
    console.log(point.quadrant); // 3

    point.angle = 280;
    console.log(point.quadrant); // 4
    ```
*   `selected`

    This property is only valid if the point is an anchor or handle point of a `Segment` or a `Curve`, or the position of an `Item`, as returned by `item.position`, `segment.point`, `segment.handleIn`, `segment.handleOut`, `curve.point1`, `curve.point2`, `curve.handle1`, `curve.handle2`.

    In those cases, it returns `true` if it the point is selected, `false` otherwise.

    Paper.js renders selected points on top of your project. This is very useful when debugging.

    * Default:
    * `false`
    * Type:
    * `Boolean`

    Example:

    ```jsx
    var path = new Path.Circle({
        center: [80, 50],
        radius: 40
    });

    // Select the third segment point:
    path.segments[2].point.selected = true;

    // Select the item's position, which is the pivot point
    // around which it is transformed:
    path.position.selected = true;
    ```

## Methods

*   `set(...values)`

    Sets the point to the passed values. Note that any sequence of parameters that is supported by the various `Point`() constructors also work for calls of `set()`.

    * Parameters:
    * `values:` `any value`
    * Returns:
    * `Point`
*   `equals(point)`

    Checks whether the coordinates of the point are equal to that of the supplied point.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Boolean` — `true` if the points are equal, `false` otherwise

    Example:

    ```jsx
    var point = new Point(5, 10);
    console.log(point == new Point(5, 10)); // true
    console.log(point == new Point(1, 1)); // false
    console.log(point != new Point(1, 1)); // true
    ```
*   `clone()`

    Returns a copy of the point.

    * Returns:
    * `Point` — the cloned point

    Example:

    ```jsx
    var point1 = new Point();
    var point2 = point1;
    point2.x = 1; // also changes point1.x

    var point2 = point1.clone();
    point2.x = 1; // doesn't change point1.x
    ```
* `toString()`
  * Returns:
  * `String` — a string representation of the point
*   `getAngle(point)`

    Returns the smaller angle between two vectors. The angle is unsigned, no information about rotational direction is given.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Number` — the angle in degrees
*   `getAngleInRadians(point)`

    Returns the smaller angle between two vectors in radians. The angle is unsigned, no information about rotational direction is given.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Number` — the angle in radians
*   `getDirectedAngle(point)`

    Returns the angle between two vectors. The angle is directional and signed, giving information about the rotational direction.

    Read more about angle units and orientation in the description of the `angle` property.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Number` — the angle between the two vectors
*   `getDistance(point[, squared])`

    Returns the distance between the point and another point.

    * Parameters:
    * `point:` `Point`
    * `squared:` `Boolean` — Controls whether the distance should remain squared, or its square root should be calculated — optional, default: `false`
    * Returns:
    * `Number`
*   `normalize([length])`

    Normalize modifies the `length` of the vector to `1` without changing its angle and returns it as a new point. The optional `length` parameter defines the length to normalize to. The object itself is not modified!

    * Parameters:
    * `length:` `Number` — The length of the normalized vector — optional, default: `1`
    * Returns:
    * `Point` — the normalized vector of the vector that is represented by this point’s coordinates
*   `rotate(angle, center)`

    Rotates the point by the given angle around an optional center point. The object itself is not modified.

    Read more about angle units and orientation in the description of the `angle` property.

    * Parameters:
    * `angle:` `Number` — the rotation angle
    * `center:` `Point` — the center point of the rotation
    * Returns:
    * `Point` — the rotated point
*   `transform(matrix)`

    Transforms the point by the matrix as a new point. The object itself is not modified!

    * Parameters:
    * `matrix:` `Matrix`
    * Returns:
    * `Point` — the transformed point

### Tests

*   `isInside(rect)`

    Checks whether the point is inside the boundaries of the rectangle.

    * Parameters:
    * `rect:` `Rectangle` — the rectangle to check against
    * Returns:
    * `Boolean` — `true` if the point is inside the rectangle, `false` otherwise
*   `isClose(point, tolerance)`

    Checks if the point is within a given distance of another point.

    * Parameters:
    * `point:` `Point` — the point to check against
    * `tolerance:` `Number` — the maximum distance allowed
    * Returns:
    * `Boolean` — `true` if it is within the given distance, `false` otherwise
*   `isCollinear(point)`

    Checks if the vector represented by this point is collinear (parallel) to another vector.

    * Parameters:
    * `point:` `Point` — the vector to check against
    * Returns:
    * `Boolean` — `true` it is collinear, `false` otherwise
*   `isOrthogonal(point)`

    Checks if the vector represented by this point is orthogonal (perpendicular) to another vector.

    * Parameters:
    * `point:` `Point` — the vector to check against
    * Returns:
    * `Boolean` — `true` it is orthogonal, `false` otherwise
*   `isZero()`

    Checks if this point has both the x and y coordinate set to 0.

    * Returns:
    * `Boolean` — `true` if both x and y are 0, `false` otherwise
*   `isNaN()`

    Checks if this point has an undefined value for at least one of its coordinates.

    * Returns:
    * `Boolean` — `true` if either x or y are not a number, `false` otherwise
*   `isInQuadrant(quadrant)`

    Checks if the vector is within the specified quadrant. Note that if the vector lies on the boundary between two quadrants, `true` will be returned for both quadrants.

    * Parameters:
    * `quadrant:` `Number` — the quadrant to check against
    * Returns:
    * `Boolean` — `true` if either x or y are not a number, `false` otherwise
    * See also:
    * `quadrant`

### Vector Math Functions

*   `dot(point)`

    Returns the dot product of the point and another point.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Number` — the dot product of the two points
*   `cross(point)`

    Returns the cross product of the point and another point.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Number` — the cross product of the two points
*   `project(point)`

    Returns the projection of the point onto another point. Both points are interpreted as vectors.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Point` — the projection of the point onto another point

### Math Functions

*   `round()`

    Returns a new point with rounded `x` and `y` values. The object itself is not modified!

    * Returns:
    * `Point`

    Example:

    ```jsx
    var point = new Point(10.2, 10.9);
    var roundPoint = point.round();
    console.log(roundPoint); // {x: 10, y: 11}
    ```
*   `ceil()`

    Returns a new point with the nearest greater non-fractional values to the specified `x` and `y` values. The object itself is not modified!

    * Returns:
    * `Point`

    Example:

    ```jsx
    var point = new Point(10.2, 10.9);
    var ceilPoint = point.ceil();
    console.log(ceilPoint); // {x: 11, y: 11}
    ```
*   `floor()`

    Returns a new point with the nearest smaller non-fractional values to the specified `x` and `y` values. The object itself is not modified!

    * Returns:
    * `Point`

    Example:

    ```jsx
    var point = new Point(10.2, 10.9);
    var floorPoint = point.floor();
    console.log(floorPoint); // {x: 10, y: 10}
    ```
*   `abs()`

    Returns a new point with the absolute values of the specified `x` and `y` values. The object itself is not modified!

    * Returns:
    * `Point`

    Example:

    ```jsx
    var point = new Point(-5, 10);
    var absPoint = point.abs();
    console.log(absPoint); // {x: 5, y: 10}
    ```

### Math Operator Functions

*   `add(number)`

    Returns the addition of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to add
    * Returns:
    * `Point` — the addition of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(5, 10);
    var result = point + 20;
    console.log(result); // {x: 25, y: 30}
    ```
*   `add(point)`

    Returns the addition of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to add
    * Returns:
    * `Point` — the addition of the two points as a new point

    Example:

    ```jsx
    var point1 = new Point(5, 10);
    var point2 = new Point(10, 20);
    var result = point1 + point2;
    console.log(result); // {x: 15, y: 30}
    ```
*   `subtract(number)`

    Returns the subtraction of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to subtract
    * Returns:
    * `Point` — the subtraction of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(10, 20);
    var result = point - 5;
    console.log(result); // {x: 5, y: 15}
    ```
*   `subtract(point)`

    Returns the subtraction of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to subtract
    * Returns:
    * `Point` — the subtraction of the two points as a new point

    Example:

    ```jsx
    var firstPoint = new Point(10, 20);
    var secondPoint = new Point(5, 5);
    var result = firstPoint - secondPoint;
    console.log(result); // {x: 5, y: 15}
    ```
*   `multiply(number)`

    Returns the multiplication of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to multiply by
    * Returns:
    * `Point` — the multiplication of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(10, 20);
    var result = point * 2;
    console.log(result); // {x: 20, y: 40}
    ```
*   `multiply(point)`

    Returns the multiplication of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to multiply by
    * Returns:
    * `Point` — the multiplication of the two points as a new point

    Example:

    ```jsx
    var firstPoint = new Point(5, 10);
    var secondPoint = new Point(4, 2);
    var result = firstPoint * secondPoint;
    console.log(result); // {x: 20, y: 20}
    ```
*   `divide(number)`

    Returns the division of the supplied value to both coordinates of the point as a new point. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to divide by
    * Returns:
    * `Point` — the division of the point and the value as a new point

    Example:

    ```jsx
    var point = new Point(10, 20);
    var result = point / 2;
    console.log(result); // {x: 5, y: 10}
    ```
*   `divide(point)`

    Returns the division of the supplied point to the point as a new point. The object itself is not modified!

    * Parameters:
    * `point:` `Point` — the point to divide by
    * Returns:
    * `Point` — the division of the two points as a new point

    Example:

    ```jsx
    var firstPoint = new Point(8, 10);
    var secondPoint = new Point(2, 5);
    var result = firstPoint / secondPoint;
    console.log(result); // {x: 4, y: 2}
    ```
*   `modulo(value)`

    The modulo operator returns the integer remainders of dividing the point by the supplied value as a new point.

    * Parameters:
    * `value:` `Number`
    * Returns:
    * `Point` — the integer remainders of dividing the point by the value as a new point

    Example:

    ```jsx
    var point = new Point(12, 6);
    console.log(point % 5); // {x: 2, y: 1}
    ```
*   `modulo(point)`

    The modulo operator returns the integer remainders of dividing the point by the supplied value as a new point.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Point` — the integer remainders of dividing the points by each other as a new point

    Example:

    ```jsx
    var point = new Point(12, 6);
    console.log(point % new Point(5, 2)); // {x: 2, y: 0}
    ```

## Static Methods

*   `Point.min(point1, point2)`

    Returns a new point object with the smallest `x` and `y` of the supplied points.

    * Parameters:
    * `point1:` `Point`
    * `point2:` `Point`
    * Returns:
    * `Point` — the newly created point object

    Example:

    ```jsx
    var point1 = new Point(10, 100);
    var point2 = new Point(200, 5);
    var minPoint = Point.min(point1, point2);
    console.log(minPoint); // {x: 10, y: 5}
    ```

    Example:Find the minimum of multiple points:

    ```jsx
    var point1 = new Point(60, 100);
    var point2 = new Point(200, 5);
    var point3 = new Point(250, 35);
    [point1, point2, point3].reduce(Point.min) // {x: 60, y: 5}
    ```
*   `Point.max(point1, point2)`

    Returns a new point object with the largest `x` and `y` of the supplied points.

    * Parameters:
    * `point1:` `Point`
    * `point2:` `Point`
    * Returns:
    * `Point` — the newly created point object

    Example:

    ```jsx
    var point1 = new Point(10, 100);
    var point2 = new Point(200, 5);
    var maxPoint = Point.max(point1, point2);
    console.log(maxPoint); // {x: 200, y: 100}
    ```

    Example:Find the maximum of multiple points:

    ```jsx
    var point1 = new Point(60, 100);
    var point2 = new Point(200, 5);
    var point3 = new Point(250, 35);
    [point1, point2, point3].reduce(Point.max) // {x: 250, y: 100}
    ```
*   `Point.random()`

    Returns a point object with random `x` and `y` values between `0` and `1`.

    * Returns:
    * `Point` — the newly created point object

    Example:

    ```jsx
    var maxPoint = new Point(100, 100);
    var randomPoint = Point.random();

    // A point between {x:0, y:0} and {x:100, y:100}:
    var point = maxPoint * randomPoint;
    ```
