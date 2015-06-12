# Geolocation

### Description

Phonegap Boilerplate provides some helpers to easily add geolocation features to
your app.

### Geolocation : `core/utils/GeolocationHelper.js`

`GeolocationHelper` lets you easily manage geolocation tracking. An instance is available globally via `app/singletons/geolocation.js`.

__Usage :__

```js
define(['app/singletons/geolocation'], function (geolocation) {

    // Start the geolocation tracking, trigger a 'trackingStart' event
    geolocation.startTracking();

    // Stop the geolocation tracking, trigger a 'trackingStop' event
    geolocation.startTracking();

    // Listen to 'locationSuccess' event (triggered when a new position)
    // is found.
    // position is a Position object
    // http://docs.phonegap.com/en/edge/cordova_geolocation_geolocation.md.html#Position
    geolocation.on('locationSuccess', function (position) {
        console.log(position.coords.latitude position.coords.longitude);
    });

    // Listen to 'locationError' event (triggered when a geolocation error occur)
    geolocation.on('locationError', function (position) {
        console.log(position.coords.latitude position.coords.longitude);
    });

    // Return true if tracking is activated
    geolocation.isTracking();

    // Return the last cached position (never expire)
    geolocation.getLastPosition();

});
```

`GeolocationHelper` also provide a static method to calculate the distance between two points on Earth :

```js

var pointA = { latitude: 5.4, longitude: 2.3 };
var pointB = { latitude: 5.3, longitude: 2.2 };

// Returns distance between A and B in meters.
GeolocationHelper.getDistanceBetween(pointA, pointB);
```
