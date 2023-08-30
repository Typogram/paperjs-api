# Segment

The Segment object represents the points of a path through which its [`Curve`](curve.md) objects pass. The segments of a path can be accessed through its `path.segments` array.

Each segment consists of an anchor point (`segment.point`) and optionaly an incoming and an outgoing handle (`segment.handleIn` and `segment.handleOut`), describing the tangents of the two `Curve` objects that are connected by this segment.

## Constructors

*   `Segment([point[, handleIn[, handleOut]]])`

    Creates a new Segment object.

    * Parameters:
    * `point:` `Point` — the anchor point of the segment — optional, default: `{x: 0, y: 0}`
    * `handleIn:` `Point` — the handle point relative to the anchor point of the segment that describes the in tangent of the segment — optional, default: `{x: 0, y: 0}`
    * `handleOut:` `Point` — the handle point relative to the anchor point of the segment that describes the out tangent of the segment — optional, default: `{x: 0, y: 0}`
    * Returns:
    * `Segment`

    Example:

    ```jsx
    var handleIn = new Point(-80, -100);
    var handleOut = new Point(80, 100);

    var firstPoint = new Point(100, 50);
    var firstSegment = new Segment(firstPoint, null, handleOut);

    var secondPoint = new Point(300, 50);
    var secondSegment = new Segment(secondPoint, handleIn, null);

    var path = new Path(firstSegment, secondSegment);
    path.strokeColor = 'black';
    ```
*   `Segment(object)`

    Creates a new Segment object.

    * Parameters:
    * `object:` `Object` — an object containing properties to be set on the segment
    * Returns:
    * `Segment`

    Example:Creating segments using object notation:

    ```jsx
    var firstSegment = new Segment({
        point: [100, 50],
        handleOut: [80, 100]
    });

    var secondSegment = new Segment({
        point: [300, 50],
        handleIn: [-80, -100]
    });

    var path = new Path({
        segments: [firstSegment, secondSegment],
        strokeColor: 'black'
    });
    ```

## Properties

*   `point`

    The anchor point of the segment.

    * Type:
    * `Point`
*   `handleIn`

    The handle point relative to the anchor point of the segment that describes the in tangent of the segment.

    * Type:
    * `Point`
*   `handleOut`

    The handle point relative to the anchor point of the segment that describes the out tangent of the segment.

    * Type:
    * `Point`
*   `selected`

    Specifies whether the segment is selected.

    * Type:
    * `Boolean`

    Example:

    ```jsx
    var path = new Path.Circle({
        center: [80, 50],
        radius: 40
    });

    // Select the third segment point:
    path.segments[2].selected = true;
    ```

### Hierarchy

*   `index`

    The index of the segment in the `path.segments` array that the segment belongs to.

    Read only.

    * Type:
    * `Number`
*   `path`

    The path that the segment belongs to.

    Read only.

    * Type:
    * `Path`
*   `curve`

    The curve that the segment belongs to. For the last segment of an open path, the previous segment is returned.

    Read only.

    * Type:
    * `Curve`
*   `location`

    The curve location that describes this segment’s position on the path.

    Read only.

    * Type:
    * `CurveLocation`

### Sibling Segments

*   `next`

    The next segment in the `path.segments` array that the segment belongs to. If the segments belongs to a closed path, the first segment is returned for the last segment of the path.

    Read only.

    * Type:
    * `Segment`
*   `previous`

    The previous segment in the `path.segments` array that the segment belongs to. If the segments belongs to a closed path, the last segment is returned for the first segment of the path.

    Read only.

    * Type:
    * `Segment`

## Methods

*   `hasHandles()`

    Checks if the segment has any curve handles set.

    * Returns:
    * `Boolean` — `true` if the segment has handles set, `false` otherwise
    * See also:
    * `segment.handleIn`
    * `segment.handleOut`
    * `curve.hasHandles`()
    * `path.hasHandles`()
*   `isSmooth()`

    Checks if the segment connects two curves smoothly, meaning that its two handles are collinear and segment does not form a corner.

    * Returns:
    * `Boolean` — `true` if the segment is smooth, `false` otherwise
    * See also:
    * `point.isCollinear`()
*   `clearHandles()`

    Clears the segment’s handles by setting their coordinates to zero, turning the segment into a corner.
*   `smooth([options])`

    Smooths the bezier curves that pass through this segment by taking into account the segment’s position and distance to the neighboring segments and changing the direction and length of the segment’s handles accordingly without moving the segment itself.

    Two different smoothing methods are available:

    *   `'catmull-rom'` uses the Catmull-Rom spline to smooth the segment.

        The optionally passed factor controls the knot parametrization of the algorithm:

        * `0.0`: the standard, uniform Catmull-Rom spline
        * `0.5`: the centripetal Catmull-Rom spline, guaranteeing no self-intersections
        * `1.0`: the chordal Catmull-Rom spline
    *   `'geometric'` use a simple heuristic and empiric geometric method to smooth the segment’s handles. The handles were weighted, meaning that big differences in distances between the segments will lead to probably undesired results.

        The optionally passed factor defines the tension parameter (`0…1`), controlling the amount of smoothing as a factor by which to scale each handle.
    * Options:
    * `options.type: String` — the type of smoothing method: `‘catmull-rom’`, `‘geometric’` — default: `‘catmull-rom’`
    * `options.factor: Number` — the factor parameterizing the smoothing method — default: `0.5` for `'catmull-rom'`, `0.4` for `'geometric'`
    * Parameters:
    * `options:` `Object` — the smoothing options — optional
    * See also:
    * `pathItem.smooth([options])`
*   `isFirst()`

    Checks if the this is the first segment in the `path.segments` array.

    * Returns:
    * `Boolean` — `true` if this is the first segment, `false` otherwise
*   `isLast()`

    Checks if the this is the last segment in the `path.segments` array.

    * Returns:
    * `Boolean` — `true` if this is the last segment, `false` otherwise
*   `reverse()`

    Reverses the `handleIn` and `handleOut` vectors of this segment, modifying the actual segment without creating a copy.

    * Returns:
    * `Segment` — the reversed segment
*   `reversed()`

    Returns the reversed the segment, without modifying the segment itself.

    * Returns:
    * `Segment` — the reversed segment
*   `remove()`

    Removes the segment from the path that it belongs to.

    * Returns:
    * `Boolean` — `true` if the segment was removed, `false` otherwise
* `clone()`
  * Returns:
  * `Segment`
* `toString()`
  * Returns:
  * `String` — a string representation of the segment
*   `transform(matrix)`

    Transform the segment by the specified matrix.

    * Parameters:
    * `matrix:` `Matrix` — the matrix to transform the segment by
*   `interpolate(from, to, factor)`

    Interpolates between the two specified segments and sets the point and handles of this segment accordingly.

    * Parameters:
    * `from:` `Segment` — the segment defining the geometry when `factor` is `0`
    * `to:` `Segment` — the segment defining the geometry when `factor` is `1`
    * `factor:` `Number` — the interpolation coefficient, typically between `0` and `1`, but extrapolation is possible too
