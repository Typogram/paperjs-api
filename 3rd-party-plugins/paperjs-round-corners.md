---
description: A library that provides methods to round the corners of paths in Paper.js.
---

# paperjs-round-corners

[![npm](https://img.shields.io/npm/v/paperjs-round-corners.svg)](https://www.npmjs.com/package/paperjs-round-corners)

`paperjs-round-corners` is a library that provides methods to round the corners of paths in Paper.js. It offers three different rounding methods: "simple-cubic", "cubic", and "arc", allowing you to achieve smooth and visually appealing rounded corners in your Paper.js projects.

For more information and usage examples, please visit the [npm package page](https://www.npmjs.com/package/paperjs-round-corners).

### Installation

To install `paperjs-round-corners`, use the following command:

```bash
npm install paperjs-round-corners
```

Make sure you have Paper.js installed as well.

### Getting Started

To use `paperjs-round-corners` in your Paper.js project, follow these steps:

1. Import the library and Paper.js:

```javascript
import paper from 'paper';
import { PaperRoundCorners } from 'paperjs-round-corners';
```

2. Set up your Paper.js project and create a path:

```javascript
paper.setup(canvas);
const path = new paper.Path();
// Add segments to the path
```

3. Round the corners of the path using one of the available methods:

```javascript
const roundness = 10; // Adjust the roundness value as needed
const options = { method: 'cubic' }; // Choose the desired rounding method

// Round a single segment
PaperRoundCorners.round(path.segments[0], roundness, options);

// Round multiple segments
PaperRoundCorners.roundMany(path.segments, roundness, options);
```

4. Update the Paper.js view to see the rounded path:

```javascript
paper.view.update();
```

### API Reference

### `.round(segment, roundness, options)`

Rounds the corners of a single segment.

* `segment` (paper.Segment): The segment to be rounded.
* `roundness` (number): The roundness value. Must be positive.
* `options` (object): The rounding options.
  * `method` (string): The rounding method. Can be "simple-cubic", "cubic", or "arc".

Returns `true` if the rounding was successful, `false` otherwise.

### `.roundMany(segments, roundness, options)`

Rounds the corners of multiple segments.

* `segments` (paper.Segment\[]): An array of segments to be rounded.
* `roundness` (number): The roundness value. Must be positive.
* `options` (object): The rounding options.
  * `method` (string): The rounding method. Can be "simple-cubic", "cubic", or "arc".

Returns an array of boolean values indicating the success of rounding for each segment.

### `.roundMap(segments, options)`

Rounds the corners of multiple segments using a Map.

* `segments` (Map\<paper.Segment, number>): A Map where the keys are the segments to be rounded and the values are the corresponding roundness values.
* `options` (object): The rounding options.
  * `method` (string): The rounding method. Can be "simple-cubic", "cubic", or "arc".

Returns a Map\<paper.Segment, boolean> indicating the success of rounding for each segment.

### Rounding Methods

#### <mark style="color:blue;">`simple-cubic`</mark>

The "simple-cubic" method rounds the corner by dividing the path at a specified distance (roundness) before and after the segment. It creates a smooth curve using a simple cubic Bézier curve.

#### <mark style="color:blue;">`cubic`</mark>

The "cubic" method rounds the corner by dividing the path at a specified distance (roundness) before and after the segment. It calculates the tangent lines at the division points and finds their intersection point to create a more precise and smoother curve using a cubic Bézier curve.

#### <mark style="color:blue;">`arc`</mark>

The "arc" method rounds the corner using an arc with a specified radius. It creates offset paths (inward and outward) for the curves before and after the segment, finds the intersection point between the offset paths, and creates an arc using that intersection point as the center.
