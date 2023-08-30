# Style

Style is used for changing the visual styles of items contained within a Paper.js project and is returned by `item.style` and `project.currentStyle`.

All properties of Style are also reflected directly in `Item`, i.e.: `item.fillColor`.

To set multiple style properties in one go, you can pass an object to `item.style`. This is a convenient way to define a style once and apply it to a series of items:

Example: Styling paths

```jsx
var path = new Path.Circle(new Point(80, 50), 30);
path.style = {
    fillColor: new Color(1, 0, 0),
    strokeColor: 'black',
    strokeWidth: 5
};
```

Example: Styling text items

```jsx
var text = new PointText(view.center);
text.content = 'Hello world.';
text.style = {
    fontFamily: 'Courier New',
    fontWeight: 'bold',
    fontSize: 20,
    fillColor: 'red',
    justification: 'center'
};
```

Example: Styling groups

```jsx
var path1 = new Path.Circle({
    center: [100, 50],
    radius: 30
});

var path2 = new Path.Rectangle({
    from: [170, 20],
    to: [230, 80]
});

var group = new Group(path1, path2);

// All styles set on a group are automatically
// set on the children of the group:
group.style = {
    strokeColor: 'black',
    dashArray: [4, 10],
    strokeWidth: 4,
    strokeCap: 'round'
};
```

## Properties

*   `view`

    The view that this style belongs to.

    Read only.

    * Type:
    * `View`

### Stroke Style

*   `strokeColor`

    The color of the stroke.

    * Type:
    * `Color`⟋`null`

    Example:Setting the stroke color of a path:

    ```jsx
    // Create a circle shaped path at { x: 80, y: 50 }
    // with a radius of 35:
    var circle = new Path.Circle(new Point(80, 50), 35);

    // Set its stroke color to RGB red:
    circle.strokeColor = new Color(1, 0, 0);
    ```
*   `strokeWidth`

    The width of the stroke.

    * Default:
    * `1`
    * Type:
    * `Number`

    Example:Setting an item's stroke width:

    ```jsx
    // Create a circle shaped path at { x: 80, y: 50 }
    // with a radius of 35:
    var circle = new Path.Circle(new Point(80, 50), 35);

    // Set its stroke color to black:
    circle.strokeColor = 'black';

    // Set its stroke width to 10:
    circle.strokeWidth = 10;
    ```
*   `strokeCap`

    The shape to be used at the beginning and end of open `Path` items, when they have a stroke.

    * Values:
    * `'round'`, `'square'`, `'butt'`
    * Default:
    * `'butt'`
    * Type:
    * `String`

    Example:A look at the different stroke caps:

    ```jsx
    var line = new Path(new Point(80, 50), new Point(420, 50));
    line.strokeColor = 'black';
    line.strokeWidth = 20;

    // Select the path, so we can see where the stroke is formed:
    line.selected = true;

    // Set the stroke cap of the line to be round:
    line.strokeCap = 'round';

    // Copy the path and set its stroke cap to be square:
    var line2 = line.clone();
    line2.position.y += 50;
    line2.strokeCap = 'square';

    // Make another copy and set its stroke cap to be butt:
    var line2 = line.clone();
    line2.position.y += 100;
    line2.strokeCap = 'butt';
    ```
*   `strokeJoin`

    The shape to be used at the segments and corners of `Path` items when they have a stroke.

    * Values:
    * `'miter'`, `'round'`, `'bevel'`
    * Default:
    * `'miter'`
    * Type:
    * `String`

    Example:A look at the different stroke joins:

    ```jsx
    var path = new Path();
    path.add(new Point(80, 100));
    path.add(new Point(120, 40));
    path.add(new Point(160, 100));
    path.strokeColor = 'black';
    path.strokeWidth = 20;

    // Select the path, so we can see where the stroke is formed:
    path.selected = true;

    var path2 = path.clone();
    path2.position.x += path2.bounds.width * 1.5;
    path2.strokeJoin = 'round';

    var path3 = path2.clone();
    path3.position.x += path3.bounds.width * 1.5;
    path3.strokeJoin = 'bevel';
    ```
*   `strokeScaling`

    Specifies whether the stroke is to be drawn taking the current affine transformation into account (the default behavior), or whether it should appear as a non-scaling stroke.

    * Default:
    * `true`
    * Type:
    * `Boolean`
*   `dashOffset`

    The dash offset of the stroke.

    * Default:
    * `0`
    * Type:
    * `Number`
*   `dashArray`

    Specifies an array containing the dash and gap lengths of the stroke.

    * Default:
    * `[]`
    * Type:
    * Array of `Numbers`

    Example:

    ```jsx
    var path = new Path.Circle(new Point(80, 50), 40);
    path.strokeWidth = 2;
    path.strokeColor = 'black';

    // Set the dashed stroke to [10pt dash, 4pt gap]:
    path.dashArray = [10, 4];
    ```
*   `miterLimit`

    The miter limit of the stroke. When two line segments meet at a sharp angle and miter joins have been specified for `strokeJoin`, it is possible for the miter to extend far beyond the `strokeWidth` of the path. The miterLimit imposes a limit on the ratio of the miter length to the `strokeWidth`.

    * Default:
    * `10`
    * Type:
    * `Number`

### Fill Style

*   `fillColor`

    The fill color.

    * Type:
    * `Color`⟋`null`

    Example:Setting the fill color of a path to red:

    ```jsx
    // Create a circle shaped path at { x: 80, y: 50 }
    // with a radius of 35:
    var circle = new Path.Circle(new Point(80, 50), 35);

    // Set the fill color of the circle to RGB red:
    circle.fillColor = new Color(1, 0, 0);
    ```
*   `fillRule`

    The fill-rule with which the shape gets filled. Please note that only modern browsers support fill-rules other than `'nonzero'`.

    * Values:
    * `'nonzero'`, `'evenodd'`
    * Default:
    * `'nonzero'`
    * Type:
    * `String`

### Shadow Style

*   `shadowColor`

    The shadow color.

    * Type:
    * `Color`⟋`null`

    Example:Creating a circle with a black shadow:

    ```jsx
    var circle = new Path.Circle({
        center: [80, 50],
        radius: 35,
        fillColor: 'white',
        // Set the shadow color of the circle to RGB black:
        shadowColor: new Color(0, 0, 0),
        // Set the shadow blur radius to 12:
        shadowBlur: 12,
        // Offset the shadow by { x: 5, y: 5 }
        shadowOffset: new Point(5, 5)
    });
    ```
*   `shadowBlur`

    The shadow’s blur radius.

    * Default:
    * `0`
    * Type:
    * `Number`
*   `shadowOffset`

    The shadow’s offset.

    * Default:
    * `0`
    * Type:
    * `Point`

### Selection Style

*   `selectedColor`

    The color the item is highlighted with when selected. If the item does not specify its own color, the color defined by its layer is used instead.

    * Type:
    * `Color`⟋`null`

### Character Style

*   `fontFamily`

    The font-family to be used in text content.

    * Default:
    * `'sans-serif'`
    * Type:
    * `String`
*   `fontWeight`

    The font-weight to be used in text content.

    * Default:
    * `'normal'`
    * Type:
    * `String`⟋`Number`
*   `fontSize`

    The font size of text content, as a number in pixels, or as a string with optional units `'px'`, `'pt'` and `'em'`.

    * Default:
    * `10`
    * Type:
    * `Number`⟋`String`
*   `leading`

    The text leading of text content.

    * Default:
    * `fontSize * 1.2`
    * Type:
    * `Number`⟋`String`

### Paragraph Style

*   `justification`

    The justification of text paragraphs.

    * Values:
    * `'left'`, `'right'`, `'center'`
    * Default:
    * `'left'`
    * Type:
    * `String`
