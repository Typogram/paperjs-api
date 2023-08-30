# Tween

Allows tweening `Object` properties between two states for a given duration. To tween properties on Paper.js `Item` instances, `item.tween(from, to, options)` can be used, which returns created tween instance.

## Constructors

*   `Tween(object, from, to, duration[, easing[, start]])`

    Creates a new tween.

    * Parameters:
    * `object:` `Object` — the object to tween the properties on
    * `from:` `Object` — the state at the start of the tweening
    * `to:` `Object` — the state at the end of the tweening
    * `duration:` `Number` — the duration of the tweening
    * `easing:` `String`⟋`Function` — the type of the easing function or the easing function — optional, default: `‘linear’`
    * `start:` `Boolean` — whether to start tweening automatically — optional, default: `true`
    * Returns:
    * `Tween` — the newly created tween

## Properties

### Event Handlers

*   `onUpdate`

    The function to be called when the tween is updated. It receives an object as its sole argument, containing the current progress of the tweening and the factor calculated by the easing function.

    * Type:
    * `Function`⟋`null`

    Example:Display tween progression values:

    ```jsx
    var circle = new Path.Circle({
        center: view.center,
        radius: 40,
        fillColor: 'blue'
    });
    var tween = circle.tweenTo(
        { fillColor: 'red' },
        {
            duration: 2000,
            easing: 'easeInCubic'
        }
    );
    var progressText = new PointText(view.center + [60, -10]);
    var factorText = new PointText(view.center + [60, 10]);

    // Install event using onUpdate() property:
    tween.onUpdate = function(event) {
        progressText.content = 'progress: ' + event.progress.toFixed(2);
    };

    // Install event using on('update') method:
    tween.on('update', function(event) {
        factorText.content = 'factor: ' + event.factor.toFixed(2);
    });
    ```

## Methods

*   `then(function)`

    Set a function that will be executed when the tween completes.

    * Parameters:
    * `function:` `Function` — the function to execute when the tween completes
    * Returns:
    * `Tween`

    Example:Tweens chaining:

    ```jsx
    var circle = new Path.Circle({
        center: view.center,
        radius: 40,
        fillColor: 'blue'
    });
    // Tween color from blue to red.
    var tween = circle.tweenTo({ fillColor: 'red' }, 2000);
    // When the first tween completes...
    tween.then(function() {
        // ...tween color back to blue.
        circle.tweenTo({ fillColor: 'blue' }, 2000);
    });
    ```
*   `start()`

    Start tweening.

    * Returns:
    * `Tween`

    Example:Manually start tweening.

    ```jsx
    var circle = new Path.Circle({
        center: view.center,
        radius: 40,
        fillColor: 'blue'
    });
    var tween = circle.tweenTo(
        { fillColor: 'red' },
        { duration: 2000, start: false }
    );
    tween.start();
    ```
*   `stop()`

    Stop tweening.

    * Returns:
    * `Tween`

    Example:Stop a tween before it completes.

    ```jsx
    var circle = new Path.Circle({
        center: view.center,
        radius: 40,
        fillColor: 'blue'
    });
    // Start tweening from blue to red for 2 seconds.
    var tween = circle.tweenTo({ fillColor: 'red' }, 2000);
    // After 1 second...
    setTimeout(function(){
        // ...stop tweening.
        tween.stop();
    }, 1000);
    ```
