# Matrix

An affine transformation matrix performs a linear mapping from 2D coordinates to other 2D coordinates that preserves the “straightness” and “parallelness” of lines.

Such a coordinate transformation can be represented by a 3 row by 3 column matrix with an implied last row of `[ 0 0 1 ]`. This matrix transforms source coordinates `(x, y)` into destination coordinates `(x',y')` by considering them to be a column vector and multiplying the coordinate vector by the matrix according to the following process:

```
[ x ]   [ a  c  tx ] [ x ]   [ a * x + c * y + tx ]
[ y ] = [ b  d  ty ] [ y ] = [ b * x + d * y + ty ]
[ 1 ]   [ 0  0  1  ] [ 1 ]   [         1          ]
```

Note the locations of b and c.

This class is optimized for speed and minimizes calculations based on its knowledge of the underlying matrix (as opposed to say simply performing matrix multiplication).

## Constructors

*   `Matrix()`

    Creates a 2D affine transformation matrix that describes the identity transformation.

    * Returns:
    * `Matrix`
*   `Matrix(a, b, c, d, tx, ty)`

    Creates a 2D affine transformation matrix.

    * Parameters:
    * `a:` `Number` — the a property of the transform
    * `b:` `Number` — the b property of the transform
    * `c:` `Number` — the c property of the transform
    * `d:` `Number` — the d property of the transform
    * `tx:` `Number` — the tx property of the transform
    * `ty:` `Number` — the ty property of the transform
    * Returns:
    * `Matrix`
*   `Matrix(values)`

    Creates a 2D affine transformation matrix.

    * Parameters:
    * `values:` Array of `Numbers` — the matrix values to initialize this matrix with
    * Returns:
    * `Matrix`
*   `Matrix(matrix)`

    Creates a 2D affine transformation matrix.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to copy the values from
    * Returns:
    * `Matrix`

## Properties

*   `a`

    The value that affects the transformation along the x axis when scaling or rotating, positioned at (0, 0) in the transformation matrix.

    * Type:
    * `Number`
*   `b`

    The value that affects the transformation along the y axis when rotating or skewing, positioned at (1, 0) in the transformation matrix.

    * Type:
    * `Number`
*   `c`

    The value that affects the transformation along the x axis when rotating or skewing, positioned at (0, 1) in the transformation matrix.

    * Type:
    * `Number`
*   `d`

    The value that affects the transformation along the y axis when scaling or rotating, positioned at (1, 1) in the transformation matrix.

    * Type:
    * `Number`
*   `tx`

    The distance by which to translate along the x axis, positioned at (2, 0) in the transformation matrix.

    * Type:
    * `Number`
*   `ty`

    The distance by which to translate along the y axis, positioned at (2, 1) in the transformation matrix.

    * Type:
    * `Number`
*   `values`

    The matrix values as an array, in the same sequence as they are passed to `initialize(a, b, c, d, tx, ty)`.

    Read only.

    * Type:
    * Array of `Numbers`
*   `translation`

    The translation of the matrix as a vector.

    Read only.

    * Type:
    * `Point`
*   `scaling`

    The scaling values of the matrix, if it can be decomposed.

    Read only.

    * Type:
    * `Point`
    * See also:
    * `decompose`()
*   `rotation`

    The rotation angle of the matrix, if it can be decomposed.

    Read only.

    * Type:
    * `Number`
    * See also:
    * `decompose`()

## Methods

*   `set(...values)`

    Sets the matrix to the passed values. Note that any sequence of parameters that is supported by the various `Matrix`() constructors also work for calls of `set()`.

    * Parameters:
    * `values:` `any value`
    * Returns:
    * `Point`
* `clone()`
  * Returns:
  * `Matrix` — a copy of this transform
*   `equals(matrix)`

    Checks whether the two matrices describe the same transformation.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to compare this matrix to
    * Returns:
    * `Boolean` — `true` if the matrices are equal, `false` otherwise
* `toString()`
  * Returns:
  * `String` — a string representation of this transform
*   `reset()`

    Resets the matrix by setting its values to the ones of the identity matrix that results in no transformation.
*   `apply([recursively])`

    Attempts to apply the matrix to the content of item that it belongs to, meaning its transformation is baked into the item’s content or children.

    * Parameters:
    * `recursively:` `Boolean` — controls whether to apply transformations recursively on children — optional, default: `true`
    * Returns:
    * `Boolean` — `true` if the matrix was applied, `false` otherwise
*   `translate(point)`

    Concatenates this matrix with a translate transformation.

    * Parameters:
    * `point:` `Point` — the vector to translate by
    * Returns:
    * `Matrix` — this affine transform
*   `translate(dx, dy)`

    Concatenates this matrix with a translate transformation.

    * Parameters:
    * `dx:` `Number` — the distance to translate in the x direction
    * `dy:` `Number` — the distance to translate in the y direction
    * Returns:
    * `Matrix` — this affine transform
*   `scale(scale[, center])`

    Concatenates this matrix with a scaling transformation.

    * Parameters:
    * `scale:` `Number` — the scaling factor
    * `center:` `Point` — the center for the scaling transformation — optional
    * Returns:
    * `Matrix` — this affine transform
*   `scale(hor, ver[, center])`

    Concatenates this matrix with a scaling transformation.

    * Parameters:
    * `hor:` `Number` — the horizontal scaling factor
    * `ver:` `Number` — the vertical scaling factor
    * `center:` `Point` — the center for the scaling transformation — optional
    * Returns:
    * `Matrix` — this affine transform
*   `rotate(angle, center)`

    Concatenates this matrix with a rotation transformation around an anchor point.

    * Parameters:
    * `angle:` `Number` — the angle of rotation measured in degrees
    * `center:` `Point` — the anchor point to rotate around
    * Returns:
    * `Matrix` — this affine transform
*   `rotate(angle, x, y)`

    Concatenates this matrix with a rotation transformation around an anchor point.

    * Parameters:
    * `angle:` `Number` — the angle of rotation measured in degrees
    * `x:` `Number` — the x coordinate of the anchor point
    * `y:` `Number` — the y coordinate of the anchor point
    * Returns:
    * `Matrix` — this affine transform
*   `shear(shear[, center])`

    Concatenates this matrix with a shear transformation.

    * Parameters:
    * `shear:` `Point` — the shear factor in x and y direction
    * `center:` `Point` — the center for the shear transformation — optional
    * Returns:
    * `Matrix` — this affine transform
*   `shear(hor, ver[, center])`

    Concatenates this matrix with a shear transformation.

    * Parameters:
    * `hor:` `Number` — the horizontal shear factor
    * `ver:` `Number` — the vertical shear factor
    * `center:` `Point` — the center for the shear transformation — optional
    * Returns:
    * `Matrix` — this affine transform
*   `skew(skew[, center])`

    Concatenates this matrix with a skew transformation.

    * Parameters:
    * `skew:` `Point` — the skew angles in x and y direction in degrees
    * `center:` `Point` — the center for the skew transformation — optional
    * Returns:
    * `Matrix` — this affine transform
*   `skew(hor, ver[, center])`

    Concatenates this matrix with a skew transformation.

    * Parameters:
    * `hor:` `Number` — the horizontal skew angle in degrees
    * `ver:` `Number` — the vertical skew angle in degrees
    * `center:` `Point` — the center for the skew transformation — optional
    * Returns:
    * `Matrix` — this affine transform
*   `append(matrix)`

    Appends the specified matrix to this matrix. This is the equivalent of multiplying `(this matrix) * (specified matrix)`.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to append
    * Returns:
    * `Matrix` — this matrix, modified
*   `prepend(matrix)`

    Prepends the specified matrix to this matrix. This is the equivalent of multiplying `(specified matrix) * (this matrix)`.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to prepend
    * Returns:
    * `Matrix` — this matrix, modified
*   `appended(matrix)`

    Returns a new matrix as the result of appending the specified matrix to this matrix. This is the equivalent of multiplying `(this matrix) * (specified matrix)`.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to append
    * Returns:
    * `Matrix` — the newly created matrix
*   `prepended(matrix)`

    Returns a new matrix as the result of prepending the specified matrix to this matrix. This is the equivalent of multiplying `(specified matrix) * (this matrix)`.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to prepend
    * Returns:
    * `Matrix` — the newly created matrix
*   `invert()`

    Inverts the matrix, causing it to perform the opposite transformation. If the matrix is not invertible (in which case `isSingular`() returns true), `null` is returned.

    * Returns:
    * `Matrix` — this matrix, or `null`, if the matrix is singular.
*   `inverted()`

    Creates a new matrix that is the inversion of this matrix, causing it to perform the opposite transformation. If the matrix is not invertible (in which case `isSingular`() returns true), `null` is returned.

    * Returns:
    * `Matrix` — this matrix, or `null`, if the matrix is singular.
* `isIdentity()`
  * Returns:
  * `Boolean` — whether this matrix is the identity matrix
*   `isInvertible()`

    Checks whether the matrix is invertible. A matrix is not invertible if the determinant is 0 or any value is infinite or NaN.

    * Returns:
    * `Boolean` — whether the matrix is invertible
*   `isSingular()`

    Checks whether the matrix is singular or not. Singular matrices cannot be inverted.

    * Returns:
    * `Boolean` — whether the matrix is singular
*   `transform(point)`

    Transforms a point and returns the result.

    * Parameters:
    * `point:` `Point` — the point to be transformed
    * Returns:
    * `Point` — the transformed point
*   `transform(src, dst, count)`

    Transforms an array of coordinates by this matrix and stores the results into the destination array, which is also returned.

    * Parameters:
    * `src:` Array of `Numbers` — the array containing the source points as x, y value pairs
    * `dst:` Array of `Numbers` — the array into which to store the transformed point pairs
    * `count:` `Number` — the number of points to transform
    * Returns:
    * `Array of Numbers` — the dst array, containing the transformed coordinates
*   `inverseTransform(point)`

    Inverse transforms a point and returns the result.

    * Parameters:
    * `point:` `Point` — the point to be transformed
    * Returns:
    * `Point`
*   `decompose()`

    Decomposes the affine transformation described by this matrix into `scaling`, `rotation` and `skewing`, and returns an object with these properties.

    * Returns:
    * `Object` — the decomposed matrix
*   `applyToContext(ctx)`

    Applies this matrix to the specified Canvas Context.

    * Parameters:
    * `ctx:` `CanvasRenderingContext2D`
