# Curve

The Curve object represents the parts of a path that are connected by two following [`Segment`](segment.md) objects. The curves of a path can be accessed through its `path.curves` array.

While a segment describe the anchor point and its incoming and outgoing handles, a Curve object describes the curve passing between two such segments. Curves and segments represent two different ways of looking at the same thing, but focusing on different aspects. Curves for example offer many convenient ways to work with parts of the path, finding lengths, positions or tangents at given offsets.

## Constructors

*   `Curve(segment1, segment2)`

    Creates a new curve object.

    * Parameters:
    * `segment1:` `Segment`
    * `segment2:` `Segment`
    * Returns:
    * `Curve`
*   `Curve(point1, handle1, handle2, point2)`

    Creates a new curve object.

    * Parameters:
    * `point1:` `Point`
    * `handle1:` `Point`
    * `handle2:` `Point`
    * `point2:` `Point`
    * Returns:
    * `Curve`

## Properties

*   `point1`

    The first anchor point of the curve.

    * Type:
    * `Point`
*   `point2`

    The second anchor point of the curve.

    * Type:
    * `Point`
*   `handle1`

    The handle point that describes the tangent in the first anchor point.

    * Type:
    * `Point`
*   `handle2`

    The handle point that describes the tangent in the second anchor point.

    * Type:
    * `Point`
*   `segment1`

    The first segment of the curve.

    Read only.

    * Type:
    * `Segment`
*   `segment2`

    The second segment of the curve.

    Read only.

    * Type:
    * `Segment`
*   `path`

    The path that the curve belongs to.

    Read only.

    * Type:
    * `Path`
*   `index`

    The index of the curve in the `path.curves` array.

    Read only.

    * Type:
    * `Number`
*   `next`

    The next curve in the `path.curves` array that the curve belongs to.

    Read only.

    * Type:
    * `Curve`
*   `previous`

    The previous curve in the `path.curves` array that the curve belongs to.

    Read only.

    * Type:
    * `Curve`
*   `selected`

    Specifies whether the points and handles of the curve are selected.

    * Type:
    * `Boolean`
*   `values`

    An array of 8 float values, describing this curve’s geometry in four absolute x/y pairs (point1, handle1, handle2, point2). This format is used internally for efficient processing of curve geometries, e.g. when calculating intersections or bounds.

    Note that the handles are converted to absolute coordinates.

    Read only.

    * Type:
    * Array of `Numbers`
*   `points`

    An array of 4 point objects, describing this curve’s geometry in absolute coordinates (point1, handle1, handle2, point2).

    Note that the handles are converted to absolute coordinates.

    Read only.

    * Type:
    * Array of `Point` objects
*   `length`

    The approximated length of the curve.

    Read only.

    * Type:
    * `Number`
*   `area`

    The area that the curve’s geometry is covering.

    Read only.

    * Type:
    * `Number`

### Bounding Boxes

*   `bounds`

    The bounding rectangle of the curve excluding stroke width.

    * Type:
    * `Rectangle`
*   `strokeBounds`

    The bounding rectangle of the curve including stroke width.

    * Type:
    * `Rectangle`
*   `handleBounds`

    The bounding rectangle of the curve including handles.

    * Type:
    * `Rectangle`

## Methods

*   `clone()`

    Returns a copy of the curve.

    * Returns:
    * `Curve`
* `toString()`
  * Returns:
  * `String` — a string representation of the curve
*   `classify()`

    Determines the type of cubic Bézier curve via discriminant classification, as well as the curve-time parameters of the associated points of inflection, loops, cusps, etc.

    * Returns:
    * `Object` — the curve classification information as an object, see options
    * `info.type: String` — the type of Bézier curve, possible values are: `‘line’`, `‘quadratic’`, `‘serpentine’`, `‘cusp’`, `‘loop’`, `‘arch’`
    * `info.roots: Array of Numbers` — the curve-time parameters of the associated points of inflection for serpentine curves, loops, cusps, etc
*   `remove()`

    Removes the curve from the path that it belongs to, by removing its second segment and merging its handle with the first segment.

    * Returns:
    * `Boolean` — `true` if the curve was removed, `false` otherwise
*   `isFirst()`

    Checks if the this is the first curve in the `path.curves` array.

    * Returns:
    * `Boolean` — `true` if this is the first curve, `false` otherwise
*   `isLast()`

    Checks if the this is the last curve in the `path.curves` array.

    * Returns:
    * `Boolean` — `true` if this is the last curve, `false` otherwise
*   `getPart(from, to)`

    Creates a new curve as a sub-curve from this curve, its range defined by the given curve-time parameters. If `from` is larger than `to`, then the resulting curve will have its direction reversed.

    * Parameters:
    * `from:` `Number` — the curve-time parameter at which the sub-curve starts
    * `to:` `Number` — the curve-time parameter at which the sub-curve ends
    * Returns:
    * `Curve` — the newly create sub-curve
*   `divideAt(location)`

    Divides the curve into two curves at the given offset or location. The curve itself is modified and becomes the first part, the second part is returned as a new curve. If the curve belongs to a path item, a new segment is inserted into the path at the given location, and the second part becomes a part of the path as well.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve at which to divide
    * Returns:
    * `Curve` — the second part of the divided curve if the location is valid, {code null} otherwise
    * See also:
    * `divideAtTime(time)`
*   `divideAtTime(time)`

    Divides the curve into two curves at the given curve-time parameter. The curve itself is modified and becomes the first part, the second part is returned as a new curve. If the modified curve belongs to a path item, the second part is also added to the path.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve at which to divide
    * Returns:
    * `Curve` — the second part of the divided curve, if the offset is within the valid range, {code null} otherwise.
    * See also:
    * `divideAt(offset)`
*   `splitAt(location)`

    Splits the path this curve belongs to at the given offset. After splitting, the path will be open. If the path was open already, splitting will result in two paths.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve at which to split
    * Returns:
    * `Path` — the newly created path after splitting, if any
    * See also:
    * `path.splitAt(offset)`
*   `splitAtTime(time)`

    Splits the path this curve belongs to at the given offset. After splitting, the path will be open. If the path was open already, splitting will result in two paths.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve at which to split
    * Returns:
    * `Path` — the newly created path after splitting, if any
    * See also:
    * `path.splitAt(offset)`
*   `reversed()`

    Returns a reversed version of the curve, without modifying the curve itself.

    * Returns:
    * `Curve` — a reversed version of the curve
*   `clearHandles()`

    Clears the curve’s handles by setting their coordinates to zero, turning the curve into a straight line.

### Curve Tests

*   `hasHandles()`

    Checks if this curve has any curve handles set.

    * Returns:
    * `Boolean` — `true` if the curve has handles set, `false` otherwise
    * See also:
    * `curve.handle1`
    * `curve.handle2`
    * `segment.hasHandles`()
    * `path.hasHandles`()
*   `hasLength([epsilon])`

    Checks if this curve has any length.

    * Parameters:
    * `epsilon:` `Number` — the epsilon against which to compare the curve’s length — optional, default: `0`
    * Returns:
    * `Boolean` — `true` if the curve is longer than the given epsilon, `false` otherwise
*   `isStraight()`

    Checks if this curve appears as a straight line. This can mean that it has no handles defined, or that the handles run collinear with the line that connects the curve’s start and end point, not falling outside of the line.

    * Returns:
    * `Boolean` — `true` if the curve is straight, `false` otherwise
*   `isLinear()`

    Checks if this curve is parametrically linear, meaning that it is straight and its handles are positioned at 1/3 and 2/3 of the total length of the curve.

    * Returns:
    * `Boolean` — `true` if the curve is parametrically linear, `false` otherwise
*   `isCollinear(curve)`

    Checks if the the two curves describe straight lines that are collinear, meaning they run in parallel.

    * Parameters:
    * `curve:` `Curve` — the other curve to check against
    * Returns:
    * `Boolean` — `true` if the two lines are collinear, `false` otherwise
*   `isHorizontal()`

    Checks if the curve is a straight horizontal line.

    * Returns:
    * `Boolean` — `true` if the line is horizontal, `false` otherwise
*   `isVertical()`

    Checks if the curve is a straight vertical line.

    * Returns:
    * `Boolean` — `true` if the line is vertical, `false` otherwise

### Positions on Curves

*   `getLocationAt(offset)`

    Calculates the curve location at the specified offset on the curve.

    * Parameters:
    * `offset:` `Number` — the offset on the curve
    * Returns:
    * `CurveLocation` — the curve location at the specified the offset
*   `getLocationAtTime(time)`

    Calculates the curve location at the specified curve-time parameter on the curve.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `CurveLocation` — the curve location at the specified the location
*   `getTimeAt(offset[, start])`

    Calculates the curve-time parameter of the specified offset on the path, relative to the provided start parameter. If offset is a negative value, the parameter is searched to the left of the start parameter. If no start parameter is provided, a default of `0` for positive values of `offset` and `1` for negative values of `offset`.

    * Parameters:
    * `offset:` `Number` — the offset at which to find the curve-time, in curve length units
    * `start:` `Number` — the curve-time in relation to which the offset is determined — optional
    * Returns:
    * `Number` — the curve-time parameter at the specified location
*   `getTimesWithTangent(tangent)`

    Calculates the curve-time parameters where the curve is tangential to provided tangent. Note that tangents at the start or end are included.

    * Parameters:
    * `tangent:` `Point` — the tangent to which the curve must be tangential
    * Returns:
    * `Array of Numbers` — at most two curve-time parameters, where the curve is tangential to the given tangent
*   `getOffsetAtTime(time)`

    Calculates the curve offset at the specified curve-time parameter on the curve.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Number` — the curve offset at the specified the location
*   `getLocationOf(point)`

    Returns the curve location of the specified point if it lies on the curve, `null` otherwise.

    * Parameters:
    * `point:` `Point` — the point on the curve
    * Returns:
    * `CurveLocation` — the curve location of the specified point
*   `getOffsetOf(point)`

    Returns the length of the path from its beginning up to up to the specified point if it lies on the path, `null` otherwise.

    * Parameters:
    * `point:` `Point` — the point on the path
    * Returns:
    * `Number` — the length of the path up to the specified point
*   `getTimeOf(point)`

    Returns the curve-time parameter of the specified point if it lies on the curve, `null` otherwise. Note that if there is more than one possible solution in a self-intersecting curve, the first found result is returned.

    * Parameters:
    * `point:` `Point` — the point on the curve
    * Returns:
    * `Number` — the curve-time parameter of the specified point
*   `getNearestLocation(point)`

    Returns the nearest location on the curve to the specified point.

    * Parameters:
    * `point:` `Point` — the point for which we search the nearest location
    * Returns:
    * `CurveLocation` — the location on the curve that’s the closest to the specified point
*   `getNearestPoint(point)`

    Returns the nearest point on the curve to the specified point.

    * Parameters:
    * `point:` `Point` — the point for which we search the nearest point
    * Returns:
    * `Point` — the point on the curve that’s the closest to the specified point
*   `getPointAt(location)`

    Calculates the point on the curve at the given location.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve
    * Returns:
    * `Point` — the point on the curve at the given location
*   `getTangentAt(location)`

    Calculates the normalized tangent vector of the curve at the given location.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve
    * Returns:
    * `Point` — the normalized tangent of the curve at the given location
*   `getNormalAt(location)`

    Calculates the normal vector of the curve at the given location.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve
    * Returns:
    * `Point` — the normal of the curve at the given location
*   `getWeightedTangentAt(location)`

    Calculates the weighted tangent vector of the curve at the given location, its length reflecting the curve velocity at that location.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve
    * Returns:
    * `Point` — the weighted tangent of the curve at the given location
*   `getWeightedNormalAt(location)`

    Calculates the weighted normal vector of the curve at the given location, its length reflecting the curve velocity at that location.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve
    * Returns:
    * `Point` — the weighted normal of the curve at the given location
*   `getCurvatureAt(location)`

    Calculates the curvature of the curve at the given location. Curvatures indicate how sharply a curve changes direction. A straight line has zero curvature, where as a circle has a constant curvature. The curve’s radius at the given location is the reciprocal value of its curvature.

    * Parameters:
    * `location:` `Number`⟋`CurveLocation` — the offset or location on the curve
    * Returns:
    * `Number` — the curvature of the curve at the given location
*   `getPointAtTime(time)`

    Calculates the point on the curve at the given location.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Point` — the point on the curve at the given location
*   `getTangentAtTime(time)`

    Calculates the normalized tangent vector of the curve at the given location.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Point` — the normalized tangent of the curve at the given location
*   `getNormalAtTime(time)`

    Calculates the normal vector of the curve at the given location.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Point` — the normal of the curve at the given location
*   `getWeightedTangentAtTime(time)`

    Calculates the weighted tangent vector of the curve at the given location, its length reflecting the curve velocity at that location.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Point` — the weighted tangent of the curve at the given location
*   `getWeightedNormalAtTime(time)`

    Calculates the weighted normal vector of the curve at the given location, its length reflecting the curve velocity at that location.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Point` — the weighted normal of the curve at the given location
*   `getCurvatureAtTime(time)`

    Calculates the curvature of the curve at the given location. Curvatures indicate how sharply a curve changes direction. A straight line has zero curvature, where as a circle has a constant curvature. The curve’s radius at the given location is the reciprocal value of its curvature.

    * Parameters:
    * `time:` `Number` — the curve-time parameter on the curve
    * Returns:
    * `Number` — the curvature of the curve at the given location
*   `getIntersections(curve)`

    Returns all intersections between two `Curve` objects as an array of `CurveLocation` objects.

    * Parameters:
    * `curve:` `Curve` — the other curve to find the intersections with (if the curve itself or `null` is passed, the self intersection of the curve is returned, if it exists)
    * Returns:
    * `Array of CurveLocation` objects — the locations of all intersections between the curves
