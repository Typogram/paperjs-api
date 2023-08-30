# Size

The Size object is used to describe the size or dimensions of something, through its `width` and `height` properties.

Example: Create a size that is 10pt wide and 5pt high, and use it to define a rectangle:

```jsx
var size = new Size(10, 5);
console.log(size.width); // 10
console.log(size.height); // 5
var rect = new Rectangle(new Point(20, 15), size);
console.log(rect); // { x: 20, y: 15, width: 10, height: 5 }
```

## Constructors

*   `Size(width, height)`

    Creates a Size object with the given width and height values.

    * Parameters:
    * `width:` `Number` — the width
    * `height:` `Number` — the height
    * Returns:
    * `Size`

    Example:Create a size that is 10pt wide and 5pt high

    ```jsx
    var size = new Size(10, 5);
    console.log(size.width); // 10
    console.log(size.height); // 5
    ```
*   `Size(array)`

    Creates a Size object using the numbers in the given array as dimensions.

    * Parameters:
    * `array:` `Array`
    * Returns:
    * `Size`

    Example:Creating a size of width: 320, height: 240 using an array of numbers:

    ```jsx
    var array = [320, 240];
    var size = new Size(array);
    console.log(size.width); // 320
    console.log(size.height); // 240
    ```
*   `Size(object)`

    Creates a Size object using the properties in the given object.

    * Parameters:
    * `object:` `Object`
    * Returns:
    * `Size`

    Example:Creating a size of width: 10, height: 20 using an object literal:

    ```jsx
    var size = new Size({
        width: 10,
        height: 20
    });
    console.log(size.width); // 10
    console.log(size.height); // 20
    ```
*   `Size(size)`

    Creates a Size object using the coordinates of the given Size object.

    * Parameters:
    * `size:` `Size`
    * Returns:
    * `Size`
*   `Size(point)`

    Creates a Size object using the `point.x` and `point.y` values of the given Point object.

    * Parameters:
    * `point:` `Point`
    * Returns:
    * `Size`

    Example:

    ```jsx
    var point = new Point(50, 50);
    var size = new Size(point);
    console.log(size.width); // 50
    console.log(size.height); // 50
    ```

## Operators

*   `+number`, `+size`

    Returns the addition of the supplied value to the width and height of the size as a new size. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to add
    * Returns:
    * `Size` — the addition of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(5, 10);
    var result = size + 20;
    console.log(result); // {width: 25, height: 30}
    ```

    Returns the addition of the width and height of the supplied size to the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to add
    * Returns:
    * `Size` — the addition of the two sizes as a new size

    Example:

    ```jsx
    var size1 = new Size(5, 10);
    var size2 = new Size(10, 20);
    var result = size1 + size2;
    console.log(result); // {width: 15, height: 30}
    ```
*   `-number`, `-size`

    Returns the subtraction of the supplied value from the width and height of the size as a new size. The object itself is not modified! The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to subtract
    * Returns:
    * `Size` — the subtraction of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(10, 20);
    var result = size - 5;
    console.log(result); // {width: 5, height: 15}
    ```

    Returns the subtraction of the width and height of the supplied size from the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to subtract
    * Returns:
    * `Size` — the subtraction of the two sizes as a new size

    Example:

    ```jsx
    var firstSize = new Size(10, 20);
    var secondSize = new Size(5, 5);
    var result = firstSize - secondSize;
    console.log(result); // {width: 5, height: 15}
    ```
*   `*number`, `*size`

    Returns the multiplication of the supplied value with the width and height of the size as a new size. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to multiply by
    * Returns:
    * `Size` — the multiplication of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(10, 20);
    var result = size * 2;
    console.log(result); // {width: 20, height: 40}
    ```

    Returns the multiplication of the width and height of the supplied size with the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to multiply by
    * Returns:
    * `Size` — the multiplication of the two sizes as a new size

    Example:

    ```jsx
    var firstSize = new Size(5, 10);
    var secondSize = new Size(4, 2);
    var result = firstSize * secondSize;
    console.log(result); // {width: 20, height: 20}
    ```
*   `/number`, `/size`

    Returns the division of the supplied value by the width and height of the size as a new size. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to divide by
    * Returns:
    * `Size` — the division of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(10, 20);
    var result = size / 2;
    console.log(result); // {width: 5, height: 10}
    ```

    Returns the division of the width and height of the supplied size by the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to divide by
    * Returns:
    * `Size` — the division of the two sizes as a new size

    Example:

    ```jsx
    var firstSize = new Size(8, 10);
    var secondSize = new Size(2, 5);
    var result = firstSize / secondSize;
    console.log(result); // {width: 4, height: 2}
    ```
*   `%number`, `%size`

    The modulo operator returns the integer remainders of dividing the size by the supplied value as a new size.

    * Parameters:
    * `value:` `Number`
    * Returns:
    * `Size` — the integer remainders of dividing the size by the value as a new size

    Example:

    ```jsx
    var size = new Size(12, 6);
    console.log(size % 5); // {width: 2, height: 1}
    ```

    The modulo operator returns the integer remainders of dividing the size by the supplied size as a new size.

    * Parameters:
    * `size:` `Size`
    * Returns:
    * `Size` — the integer remainders of dividing the sizes by each other as a new size

    Example:

    ```jsx
    var size = new Size(12, 6);
    console.log(size % new Size(5, 2)); // {width: 2, height: 0}
    ```

## Properties

*   `width`

    The width of the size

    * Type:
    * `Number`
*   `height`

    The height of the size

    * Type:
    * `Number`

## Methods

*   `set(...values)`

    Sets the size to the passed values. Note that any sequence of parameters that is supported by the various `Size`() constructors also work for calls of `set()`.

    * Parameters:
    * `values:` `any value`
    * Returns:
    * `Size`
*   `equals(size)`

    Checks whether the width and height of the size are equal to those of the supplied size.

    * Parameters:
    * `size:` `Size` — the size to compare to
    * Returns:
    * `Boolean`

    Example:

    ```jsx
    var size = new Size(5, 10);
    console.log(size == new Size(5, 10)); // true
    console.log(size == new Size(1, 1)); // false
    console.log(size != new Size(1, 1)); // true
    ```
*   `clone()`

    Returns a copy of the size.

    * Returns:
    * `Size`
* `toString()`
  * Returns:
  * `String` — a string representation of the size

### Tests

*   `isZero()`

    Checks if this size has both the width and height set to 0.

    * Returns:
    * `Boolean` — `true` if both width and height are 0, `false` otherwise
*   `isNaN()`

    Checks if the width or the height of the size are NaN.

    * Returns:
    * `Boolean` — `true` if the width or height of the size are NaN, `false` otherwise

### Math Functions

*   `round()`

    Returns a new size with rounded `width` and `height` values. The object itself is not modified!

    * Returns:
    * `Size`

    Example:

    ```jsx
    var size = new Size(10.2, 10.9);
    var roundSize = size.round();
    console.log(roundSize); // {x: 10, y: 11}
    ```
*   `ceil()`

    Returns a new size with the nearest greater non-fractional values to the specified `width` and `height` values. The object itself is not modified!

    * Returns:
    * `Size`

    Example:

    ```jsx
    var size = new Size(10.2, 10.9);
    var ceilSize = size.ceil();
    console.log(ceilSize); // {x: 11, y: 11}
    ```
*   `floor()`

    Returns a new size with the nearest smaller non-fractional values to the specified `width` and `height` values. The object itself is not modified!

    * Returns:
    * `Size`

    Example:

    ```jsx
    var size = new Size(10.2, 10.9);
    var floorSize = size.floor();
    console.log(floorSize); // {x: 10, y: 10}
    ```
*   `abs()`

    Returns a new size with the absolute values of the specified `width` and `height` values. The object itself is not modified!

    * Returns:
    * `Size`

    Example:

    ```jsx
    var size = new Size(-5, 10);
    var absSize = size.abs();
    console.log(absSize); // {x: 5, y: 10}
    ```

### Math Operator Functions

*   `add(number)`

    Returns the addition of the supplied value to the width and height of the size as a new size. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to add
    * Returns:
    * `Size` — the addition of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(5, 10);
    var result = size + 20;
    console.log(result); // {width: 25, height: 30}
    ```
*   `add(size)`

    Returns the addition of the width and height of the supplied size to the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to add
    * Returns:
    * `Size` — the addition of the two sizes as a new size

    Example:

    ```jsx
    var size1 = new Size(5, 10);
    var size2 = new Size(10, 20);
    var result = size1 + size2;
    console.log(result); // {width: 15, height: 30}
    ```
*   `subtract(number)`

    Returns the subtraction of the supplied value from the width and height of the size as a new size. The object itself is not modified! The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to subtract
    * Returns:
    * `Size` — the subtraction of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(10, 20);
    var result = size - 5;
    console.log(result); // {width: 5, height: 15}
    ```
*   `subtract(size)`

    Returns the subtraction of the width and height of the supplied size from the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to subtract
    * Returns:
    * `Size` — the subtraction of the two sizes as a new size

    Example:

    ```jsx
    var firstSize = new Size(10, 20);
    var secondSize = new Size(5, 5);
    var result = firstSize - secondSize;
    console.log(result); // {width: 5, height: 15}
    ```
*   `multiply(number)`

    Returns the multiplication of the supplied value with the width and height of the size as a new size. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to multiply by
    * Returns:
    * `Size` — the multiplication of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(10, 20);
    var result = size * 2;
    console.log(result); // {width: 20, height: 40}
    ```
*   `multiply(size)`

    Returns the multiplication of the width and height of the supplied size with the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to multiply by
    * Returns:
    * `Size` — the multiplication of the two sizes as a new size

    Example:

    ```jsx
    var firstSize = new Size(5, 10);
    var secondSize = new Size(4, 2);
    var result = firstSize * secondSize;
    console.log(result); // {width: 20, height: 20}
    ```
*   `divide(number)`

    Returns the division of the supplied value by the width and height of the size as a new size. The object itself is not modified!

    * Parameters:
    * `number:` `Number` — the number to divide by
    * Returns:
    * `Size` — the division of the size and the value as a new size

    Example:

    ```jsx
    var size = new Size(10, 20);
    var result = size / 2;
    console.log(result); // {width: 5, height: 10}
    ```
*   `divide(size)`

    Returns the division of the width and height of the supplied size by the size as a new size. The object itself is not modified!

    * Parameters:
    * `size:` `Size` — the size to divide by
    * Returns:
    * `Size` — the division of the two sizes as a new size

    Example:

    ```jsx
    var firstSize = new Size(8, 10);
    var secondSize = new Size(2, 5);
    var result = firstSize / secondSize;
    console.log(result); // {width: 4, height: 2}
    ```
*   `modulo(value)`

    The modulo operator returns the integer remainders of dividing the size by the supplied value as a new size.

    * Parameters:
    * `value:` `Number`
    * Returns:
    * `Size` — the integer remainders of dividing the size by the value as a new size

    Example:

    ```jsx
    var size = new Size(12, 6);
    console.log(size % 5); // {width: 2, height: 1}
    ```
*   `modulo(size)`

    The modulo operator returns the integer remainders of dividing the size by the supplied size as a new size.

    * Parameters:
    * `size:` `Size`
    * Returns:
    * `Size` — the integer remainders of dividing the sizes by each other as a new size

    Example:

    ```jsx
    var size = new Size(12, 6);
    console.log(size % new Size(5, 2)); // {width: 2, height: 0}
    ```

## Static Methods

*   `Size.min(size1, size2)`

    Returns a new size object with the smallest `width` and `height` of the supplied sizes.

    * Parameters:
    * `size1:` `Size`
    * `size2:` `Size`
    * Returns:
    * `Size` — the newly created size object

    Example:

    ```jsx
    var size1 = new Size(10, 100);
    var size2 = new Size(200, 5);
    var minSize = Size.min(size1, size2);
    console.log(minSize); // {width: 10, height: 5}
    ```

    Example:Find the minimum of multiple sizes:

    ```jsx
    var size1 = new Size(60, 100);
    var size2 = new Size(200, 5);
    var size3 = new Size(250, 35);
    [size1, size2, size3].reduce(Size.min) // {width: 60, height: 5}
    ```
*   `Size.max(size1, size2)`

    Returns a new size object with the largest `width` and `height` of the supplied sizes.

    * Parameters:
    * `size1:` `Size`
    * `size2:` `Size`
    * Returns:
    * `Size` — the newly created size object

    Example:

    ```jsx
    var size1 = new Size(10, 100);
    var size2 = new Size(200, 5);
    var maxSize = Size.max(size1, size2);
    console.log(maxSize); // {width: 200, height: 100}
    ```

    Example:Find the maximum of multiple sizes:

    ```jsx
    var size1 = new Size(60, 100);
    var size2 = new Size(200, 5);
    var size3 = new Size(250, 35);
    [size1, size2, size3].reduce(Size.max) // {width: 250, height: 100}
    ```
*   `Size.random()`

    Returns a size object with random `width` and `height` values between `0` and `1`.

    * Returns:
    * `Size` — the newly created size object

    Example:

    ```jsx
    var maxSize = new Size(100, 100);
    var randomSize = Size.random();
    var size = maxSize * randomSize;
    ```
