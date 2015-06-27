# Backbutton behavior

Phonegap let you override the default backbutton behaviour by listening to the
'backbutton' event. Unfortunately, there can be only one bound callback.

To get around this, Phonegap Boilerplate provide a [backbuttonManager](api/backbuttonManager.md).

### backbuttonManager

Usage :

```js
// core/singletons/backbuttonManager is required
define(['core/singletons/backbuttonManager'], function (backbuttonManager) {

    var helloWorld = function (done) {
        alert('Hello World !');

        // Call done when you're done.
        // By default, the back button move back in the history.
        // If you want to prevent this behaviour, pass false to done.
        done(false);
    };

    // Listen to backbutton
    backbuttonManager.addListener(helloWorld);

    // Stop listening
    backbuttonManager.removeListener(helloWorld);

});

```

### In AppPages

When the backbutton is pressed, the `onBackButton` method of the page you're on
is called :

```js
//...

onBackButton: function (done) {
    alert('Hello World !');
    done(false);
}

//...
```
