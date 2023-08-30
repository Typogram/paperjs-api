# Project

A Project object in Paper.js is what usually is referred to as the document: The top level object that holds all the items contained in the scene graph. As the term document is already taken in the browser context, it is called Project.

Projects allow the manipulation of the styles that are applied to all newly created items, give access to the selected items, and will in future versions offer ways to query for items in the scene graph defining specific requirements, and means to persist and load from different formats, such as SVG and PDF.

The currently active project can be accessed through the `paperScope.project` variable.

An array of all open projects is accessible through the `paperScope.projects` variable.

## Constructors

*   `Project(element)`

    Creates a Paper.js project containing one empty `Layer`, referenced by `project.activeLayer`.

    Note that when working with PaperScript, a project is automatically created for us and the `paperScope.project` variable points to it.

    * Parameters:
    * `element:` `HTMLCanvasElement`⟋`String`⟋`Size` — the HTML canvas element that should be used as the element for the view, or an ID string by which to find the element, or the size of the canvas to be created for usage in a web worker.
    * Returns:
    * `Project`

## Properties

*   `view`

    The reference to the project’s view.

    Read only.

    * Type:
    * `View`
*   `currentStyle`

    The currently active path style. All selected items and newly created items will be styled with this style.

    * Type:
    * `Style`

    Example:

    ```jsx
    project.currentStyle = {
        fillColor: 'red',
        strokeColor: 'black',
        strokeWidth: 5
    }

    // The following paths will take over all style properties of
    // the current style:
    var path = new Path.Circle(new Point(75, 50), 30);
    var path2 = new Path.Circle(new Point(175, 50), 20);
    ```

    Example:

    ```jsx
    project.currentStyle.fillColor = 'red';

    // The following path will take over the fill color we just set:
    var path = new Path.Circle(new Point(75, 50), 30);
    var path2 = new Path.Circle(new Point(175, 50), 20);
    ```
*   `index`

    The index of the project in the `paperScope.projects` list.

    Read only.

    * Type:
    * `Number`

### Project Content

*   `layers`

    The layers contained within the project.

    Read only.

    * Type:
    * Array of `Layer` objects
*   `activeLayer`

    The layer which is currently active. New items will be created on this layer by default.

    Read only.

    * Type:
    * `Layer`
*   `symbolDefinitions`

    The symbol definitions shared by all symbol items contained place ind project.

    Read only.

    * Type:
    * Array of `SymbolDefinition` objects
*   `selectedItems`

    The selected items contained within the project.

    Read only.

    * Type:
    * Array of `Item` objects

## Methods

*   `activate()`

    Activates this project, so all newly created items will be placed in it.
*   `clear()`

    Clears the project by removing all `project.layers`.
*   `isEmpty()`

    Checks whether the project has any content or not.

    * Returns:
    * `Boolean`
*   `remove()`

    Removes this project from the `paperScope.projects` list, and also removes its view, if one was defined.
*   `selectAll()`

    Selects all items in the project.
*   `deselectAll()`

    Deselects all selected items in the project.

### Hierarchy Operations

*   `addLayer(layer)`

    Adds the specified layer at the end of the this project’s `layers` list.

    * Parameters:
    * `layer:` `Layer` — the layer to be added to the project
    * Returns:
    * `Layer` — the added layer, or `null` if adding was not possible
*   `insertLayer(index, layer)`

    Inserts the specified layer at the specified index in this project’s `layers` list.

    * Parameters:
    * `index:` `Number` — the index at which to insert the layer
    * `layer:` `Layer` — the layer to be inserted in the project
    * Returns:
    * `Layer` — the added layer, or `null` if adding was not possible

### Hit-testing, Fetching and Matching Items

*   `hitTest(point[, options])`

    Performs a hit-test on the items contained within the project at the location of the specified point.

    The options object allows you to control the specifics of the hit-test and may contain a combination of the following values:

    * Options:
    * `options.tolerance: Number` — the tolerance of the hit-test — default: `paperScope.settings`.hitTolerance
    * `options.class: Function` — only hit-test against a specific item class, or any of its sub-classes, by providing the constructor function against which an `instanceof` check is performed: `Group`, `Layer`, `Path`, `CompoundPath`, `Shape`, `Raster`, `SymbolItem`, `PointText`, …
    * `options.match: Function` — a match function to be called for each found hit result: Return `true` to return the result, `false` to keep searching
    * `options.fill: Boolean` — hit-test the fill of items — default: `true`
    * `options.stroke: Boolean` — hit-test the stroke of path items, taking into account the setting of stroke color and width — default: `true`
    * `options.segments: Boolean` — hit-test for `segment.point` of `Path` items — default: `true`
    * `options.curves: Boolean` — hit-test the curves of path items, without taking the stroke color or width into account
    * `options.handles: Boolean` — hit-test for the handles (`segment.handleIn` / `segment.handleOut`) of path segments.
    * `options.ends: Boolean` — only hit-test for the first or last segment points of open path items
    * `options.position: Boolean` — hit-test the `item.position` of of items, which depends on the setting of `item.pivot`
    * `options.center: Boolean` — hit-test the `rectangle.center` of the bounding rectangle of items (`item.bounds`)
    * `options.bounds: Boolean` — hit-test the corners and side-centers of the bounding rectangle of items (`item.bounds`)
    * `options.guides: Boolean` — hit-test items that have `Item#guide` set to `true`
    * `options.selected: Boolean` — only hit selected items
    * Parameters:
    * `point:` `Point` — the point where the hit-test should be performed
    * `options:` `Object` — optional, default: `{ fill: true, stroke: true, segments: true, tolerance: settings.hitTolerance }`
    * Returns:
    * `HitResult` — a hit result object that contains more information about what exactly was hit or `null` if nothing was hit
*   `hitTestAll(point[, options])`

    Performs a hit-test on the item and its children (if it is a `Group` or `Layer`) at the location of the specified point, returning all found hits.

    The options object allows you to control the specifics of the hit- test. See `hitTest(point[, options])` for a list of all options.

    * Parameters:
    * `point:` `Point` — the point where the hit-test should be performed
    * `options:` `Object` — optional, default: `{ fill: true, stroke: true, segments: true, tolerance: settings.hitTolerance }`
    * Returns:
    * `Array of HitResult` objects — hit result objects for all hits, describing what exactly was hit or `null` if nothing was hit
    * See also:
    * `hitTest(point[, options])`;
*   `getItems(options)`

    Fetch items contained within the project whose properties match the criteria in the specified object.

    Extended matching of properties is possible by providing a comparator function or regular expression. Matching points, colors only work as a comparison of the full object, not partial matching (e.g. only providing the x- coordinate to match all points with that x-value). Partial matching does work for `item.data`.

    Matching items against a rectangular area is also possible, by setting either `options.inside` or `options.overlapping` to a rectangle describing the area in which the items either have to be fully or partly contained.

    * Options:
    * `options.recursive: Boolean` — whether to loop recursively through all children, or stop at the current level — default: `true`
    * `options.match: Function` — a match function to be called for each item, allowing the definition of more flexible item checks that are not bound to properties. If no other match properties are defined, this function can also be passed instead of the `match` object
    * `options.class: Function` — the constructor function of the item type to match against
    * `options.inside: Rectangle` — the rectangle in which the items need to be fully contained
    * `options.overlapping: Rectangle` — the rectangle with which the items need to at least partly overlap
    * Parameters:
    * `options:` `Object`⟋`Function` — the criteria to match against
    * Returns:
    * `Array of Item` objects — the list of matching items contained in the project
    * See also:
    * `item.matches(options)`
    * `item.getItems(options)`

    Example:Fetch all selected path items:

    ```jsx
    var path1 = new Path.Circle({
        center: [50, 50],
        radius: 25,
        fillColor: 'black'
    });

    var path2 = new Path.Circle({
        center: [150, 50],
        radius: 25,
        fillColor: 'black'
    });

    // Select path2:
    path2.selected = true;

    // Fetch all selected path items:
    var items = project.getItems({
        selected: true,
        class: Path
    });

    // Change the fill color of the selected path to red:
    items[0].fillColor = 'red';
    ```

    Example:Fetch all items with a specific fill color:

    ```jsx
    var path1 = new Path.Circle({
        center: [50, 50],
        radius: 25,
        fillColor: 'black'
    });

    var path2 = new Path.Circle({
        center: [150, 50],
        radius: 25,
        fillColor: 'purple'
    });

    // Fetch all items with a purple fill color:
    var items = project.getItems({
        fillColor: 'purple'
    });

    // Select the fetched item:
    items[0].selected = true;
    ```

    Example:Fetch items at a specific position:

    ```jsx
    var path1 = new Path.Circle({
        center: [50, 50],
        radius: 25,
        fillColor: 'black'
    });

    var path2 = new Path.Circle({
        center: [150, 50],
        radius: 25,
        fillColor: 'black'
    });

    // Fetch all path items positioned at {x: 150, y: 150}:
    var items = project.getItems({
        position: [150, 50]
    });

    // Select the fetched path:
    items[0].selected = true;
    ```

    Example:Fetch items using a comparator function:

    ```jsx
    // Create a circle shaped path:
    var path1 = new Path.Circle({
        center: [50, 50],
        radius: 25,
        fillColor: 'black'
    });

    // Create a circle shaped path with 50% opacity:
    var path2 = new Path.Circle({
        center: [150, 50],
        radius: 25,
        fillColor: 'black',
        opacity: 0.5
    });

    // Fetch all items whose opacity is smaller than 1
    var items = paper.project.getItems({
        opacity: function(value) {
            return value < 1;
        }
    });

    // Select the fetched item:
    items[0].selected = true;
    ```

    Example:Fetch items using a comparator function (2):

    ```jsx
    // Create a rectangle shaped path (4 segments):
    var path1 = new Path.Rectangle({
        from: [25, 25],
        to: [75, 75],
        strokeColor: 'black',
        strokeWidth: 10
    });

    // Create a line shaped path (2 segments):
    var path2 = new Path.Line({
        from: [125, 50],
        to: [175, 50],
        strokeColor: 'black',
        strokeWidth: 10
    });

    // Fetch all paths with 2 segments:
    var items = project.getItems({
        class: Path,
     segments: function(segments) {
            return segments.length == 2;
     }
    });

    // Select the fetched path:
    items[0].selected = true;
    ```

    Example:Match (nested) properties of the data property:

    ```jsx
    // Create a black circle shaped path:
    var path1 = new Path.Circle({
        center: [50, 50],
        radius: 25,
        fillColor: 'black',
        data: {
            person: {
                name: 'john',
                length: 200,
                hair: true
            }
        }
    });

    // Create a red circle shaped path:
    var path2 = new Path.Circle({
        center: [150, 50],
        radius: 25,
        fillColor: 'red',
        data: {
            person: {
                name: 'john',
                length: 180,
                hair: false
            }
        }
    });

    // Fetch all items whose data object contains a person
    // object whose name is john and length is 180:
    var items = paper.project.getItems({
        data: {
            person: {
                name: 'john',
                length: 180
            }
        }
    });

    // Select the fetched item:
    items[0].selected = true;
    ```

    Example:Match strings using regular expressions:

    ```jsx
    // Create a path named 'aardvark':
    var path1 = new Path.Circle({
        center: [50, 50],
        radius: 25,
        fillColor: 'black',
        name: 'aardvark'
    });

    // Create a path named 'apple':
    var path2 = new Path.Circle({
        center: [150, 50],
        radius: 25,
        fillColor: 'black',
        name: 'apple'
    });

    // Create a path named 'banana':
    var path2 = new Path.Circle({
        center: [250, 50],
        radius: 25,
        fillColor: 'black',
        name: 'banana'
    });

    // Fetch all items that have a name starting with 'a':
    var items = project.getItems({
        name: /^a/
    });

    // Change the fill color of the matched items:
    for (var i = 0; i < items.length; i++) {
     items[i].fillColor = 'red';
    }
    ```
*   `getItem(options)`

    Fetch the first item contained within the project whose properties match the criteria in the specified object. Extended matching is possible by providing a compare function or regular expression. Matching points, colors only work as a comparison of the full object, not partial matching (e.g. only providing the x- coordinate to match all points with that x-value). Partial matching does work for `item.data`.

    See `getItems(options)` for a selection of illustrated examples.

    * Parameters:
    * `options:` `Object`⟋`Function` — the criteria to match against
    * Returns:
    * `Item` — the first item in the project matching the given criteria

### Importing / Exporting JSON and SVG

*   `exportJSON([options])`

    Exports (serializes) the project with all its layers and child items to a JSON data object or string.

    * Options:
    * `options.asString: Boolean` — whether the JSON is returned as a `Object` or a `String` — default: `true`
    * `options.precision: Number` — the amount of fractional digits in numbers used in JSON data — default: `5`
    * Parameters:
    * `options:` `Object` — the serialization options — optional
    * Returns:
    * `String` — the exported JSON data
*   `importJSON(json)`

    Imports (deserializes) the stored JSON data into the project. Note that the project is not cleared first. You can call `project.clear`() to do so.

    * Parameters:
    * `json:` `String` — the JSON data to import from
    * Returns:
    * `Item` — the imported item
*   `exportSVG([options])`

    Exports the project with all its layers and child items as an SVG DOM, all contained in one top level SVG group node.

    * Options:
    * `options.bounds: String`⟋`Rectangle` — the bounds of the area to export, either as a string (`‘view’`, `content’`), or a `Rectangle` object: `'view'` uses the view bounds, `'content'` uses the stroke bounds of all content — default: `‘view’`
    * `options.matrix: Matrix` — the matrix with which to transform the exported content: If `options.bounds` is set to `'view'`, `paper.view.matrix` is used, for all other settings of `options.bounds` the identity matrix is used. — default: `paper.view.matrix`
    * `options.asString: Boolean` — whether a SVG node or a `String` is to be returned — default: `false`
    * `options.precision: Number` — the amount of fractional digits in numbers used in SVG data — default: `5`
    * `options.matchShapes: Boolean` — whether path items should tried to be converted to SVG shape items (rect, circle, ellipse, line, polyline, polygon), if their geometries match — default: `false`
    * `options.embedImages: Boolean` — whether raster images should be embedded as base64 data inlined in the xlink:href attribute, or kept as a link to their external URL. — default: `true`
    * Parameters:
    * `options:` `Object` — the export options — optional
    * Returns:
    * `SVGElement`⟋`String` — the project converted to an SVG node or a `String` depending on `option.asString` value
*   `importSVG(svg[, options])`

    Converts the provided SVG content into Paper.js items and adds them to the active layer of this project. Note that the project is not cleared first. You can call `project.clear`() to do so.

    * Options:
    * `options.expandShapes: Boolean` — whether imported shape items should be expanded to path items — default: `false`
    * `options.onLoad: Function` — the callback function to call once the SVG content is loaded from the given URL receiving two arguments: the converted `item` and the original `svg` data as a string. Only required when loading from external resources.
    * `options.onError: Function` — the callback function to call if an error occurs during loading. Only required when loading from external resources.
    * `options.insert: Boolean` — whether the imported items should be added to the project that `importSVG()` is called on — default: `true`
    * `options.applyMatrix: Boolean` — whether the imported items should have their transformation matrices applied to their contents or not — default: `paperScope.settings`.applyMatrix
    * Parameters:
    * `svg:` `SVGElement`⟋`String` — the SVG content to import, either as a SVG DOM node, a string containing SVG content, or a string describing the URL of the SVG file to fetch.
    * `options:` `Object` — the import options — optional
    * Returns:
    * `Item` — the newly created Paper.js item containing the converted SVG content
*   `importSVG(svg, onLoad)`

    Imports the provided external SVG file, converts it into Paper.js items and adds them to the active layer of this project. Note that the project is not cleared first. You can call `project.clear`() to do so.

    * Parameters:
    * `svg:` `SVGElement`⟋`String` — the URL of the SVG file to fetch.
    * `onLoad:` `Function` — the callback function to call once the SVG content is loaded from the given URL receiving two arguments: the converted `item` and the original `svg` data as a string. Only required when loading from external files.
    * Returns:
    * `Item` — the newly created Paper.js item containing the converted SVG content
