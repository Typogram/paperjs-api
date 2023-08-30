# CurveLocation

CurveLocation objects describe a location on [`Curve`](curve.md) objects, as defined by the curve-time `time`, a value between `0` (beginning of the curve) and `1` (end of the curve). If the curve is part of a `Path` item, its `index` inside the `path.curves` array is also provided.

The class is in use in many places, such as `path.getLocationAt(offset)`, `path.getLocationOf(point)`, `pathItem.getNearestLocation(point)`, `pathItem.getIntersections(path)`, etc.

## Constructors

*   `CurveLocation(curve, time[, point])`

    Creates a new CurveLocation object.

    * Parameters:
    * `curve:` `Curve`
    * `time:` `Number`
    * `point:` `Point` — optional
    * Returns:
    * `CurveLocation`

## Properties

*   `segment`

    The segment of the curve which is closer to the described location.

    Read only.

    * Type:
    * `Segment`
*   `curve`

    The curve that this location belongs to.

    Read only.

    * Type:
    * `Curve`
*   `path`

    The path that this locations is situated on.

    Read only.

    * Type:
    * `Path`
*   `index`

    The index of the `curve` within the `path.curves` list, if it is part of a `Path` item.

    Read only.

    * Type:
    * `Number`
*   `time`

    The curve-time parameter, as used by various bezier curve calculations. It is value between `0` (beginning of the curve) and `1` (end of the curve).

    Read only.

    * Type:
    * `Number`
*   `point`

    The point which is defined by the `curve` and `time`.

    Read only.

    * Type:
    * `Point`
*   `offset`

    The length of the path from its beginning up to the location described by this object. If the curve is not part of a path, then the length within the curve is returned instead.

    Read only.

    * Type:
    * `Number`
*   `curveOffset`

    The length of the curve from its beginning up to the location described by this object.

    Read only.

    * Type:
    * `Number`
*   `intersection`

    The curve location on the intersecting curve, if this location is the result of a call to `pathItem.getIntersections(path)` / `curve.getIntersections(curve)`.

    Read only.

    * Type:
    * `CurveLocation`
*   `tangent`

    The tangential vector to the `curve` at the given location.

    Read only.

    * Type:
    * `Point`
*   `normal`

    The normal vector to the `curve` at the given location.

    Read only.

    * Type:
    * `Point`
*   `curvature`

    The curvature of the `curve` at the given location.

    Read only.

    * Type:
    * `Number`
*   `distance`

    The distance from the queried point to the returned location.

    Read only.

    * Type:
    * `Number`
    * See also:
    * `curve.getNearestLocation(point)`
    * `pathItem.getNearestLocation(point)`

## Methods

*   `equals(location)`

    Checks whether tow CurveLocation objects are describing the same location on a path, by applying the same tolerances as elsewhere when dealing with curve-time parameters.

    * Parameters:
    * `location:` `CurveLocation`
    * Returns:
    * `Boolean` — `true` if the locations are equal, `false` otherwise
* `toString()`
  * Returns:
  * `String` — a string representation of the curve location

### Tests

*   `isTouching()`

    Checks if the location is an intersection with another curve and is merely touching the other curve, as opposed to crossing it.

    * Returns:
    * `Boolean` — `true` if the location is an intersection that is merely touching another curve, `false` otherwise
    * See also:
    * `isCrossing`()
*   `isCrossing()`

    Checks if the location is an intersection with another curve and is crossing the other curve, as opposed to just touching it.

    * Returns:
    * `Boolean` — `true` if the location is an intersection that is crossing another curve, `false` otherwise
    * See also:
    * `isTouching`()
*   `hasOverlap()`

    Checks if the location is an intersection with another curve and is part of an overlap between the two involved paths.

    * Returns:
    * `Boolean` — `true` if the location is an intersection that is part of an overlap between the two involved paths, `false` otherwise
    * See also:
    * `isCrossing`()
    * `isTouching`()
