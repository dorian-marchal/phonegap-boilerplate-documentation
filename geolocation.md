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

### User tracking : `core/utils/UserLocationTracker.js`

[UserLocationTracker](api/UserLocationTracker) lets you add a marker that follow the user on a map.

__Usage :__

```js

define(['core/utils/UserLocationTracker'],
function (UserLocationTracker) {
    var tracker = new UserLocationTracker();

    // Assign a map to the tracker (where map is a Gmaps.js instance)
    tracker.setMap(map);

    // Customize the user marker (Gmaps.js marker options)
    tracker.setMarkerIconOptions(options);

    // Start showing the user location on the map.
    // The user position is updated when the geolocation singleton
    // trigger a 'locationSuccess' event (see above).
    // This method does not start the geolocation tracking.
    tracker.start();

    // Stop showing the user location.
    // This method does not stop the geolocation tracking.
    tracker.stop();

}

```

__Note :__ Geolocation tracking and user tracking are two different things:  
- Geolocation can be started without showing the user on a map.
- When user tracking is active, geolocation can be started/stopped without the need to restart user tracking.
- When user tracking is started/stopped, geolocation is not necessarily started/stopped accordingly.
