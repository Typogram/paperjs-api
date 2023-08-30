# Line

The Line object represents..

## Constructors

*   `Line(point1, point2[, asVector, arg3, arg4])`

    Creates a Line object.

    * Parameters:
    * `point1:` `Point`
    * `point2:` `Point`
    * `asVector:` `Boolean` — optional, default: `false`
    * `arg3:`
    * `arg4:`
    * Returns:
    * `Line`

## Properties

*   `point`

    The starting point of the line.

    Read only.

    * Type:
    * `Point`
*   `vector`

    The direction of the line as a vector.

    Read only.

    * Type:
    * `Point`
*   `length`

    The length of the line.

    Read only.

    * Type:
    * `Number`

## Methods

* `intersect(line[, isInfinite])`
  * Parameters:
  * `line:` `Line`
  * `isInfinite:` `Boolean` — optional, default: `false`
  * Returns:
  * `Point` — the intersection point of the lines, `undefined` if the two lines are collinear, or `null` if they don’t intersect.
* `getSide(point[, isInfinite])`
  * Parameters:
  * `point:` `Point`
  * `isInfinite:` `Boolean` — optional, default: `false`
  * Returns:
  * `Number`
* `getDistance(point)`
  * Parameters:
  * `point:` `Point`
  * Returns:
  * `Number`
* `getSignedDistance(point)`
  * Parameters:
  * `point:` `Point`
  * Returns:
  * `Number`
