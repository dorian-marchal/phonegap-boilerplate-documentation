# Adding maps

Phonegap Boilerplate provide some helpers to easily add Google Maps in your app pages.


### Gmaps : `gmaps`

The [gmaps.js](https://hpneo.github.io/gmaps/) library can be required via the
`gmaps` module.

When `gmaps` is required, Google Maps is available via the `google.maps` global.


### Geolocation : `core/utils/GeolocationHelper`

An helper is available to ease user geolocation. An instance of this helper can be required via the `app/singletons/geolocation` module.


### User tracking : `core/utils/UserLocationTracker`

`UserLocationTracker` is a helper used to track a user device and display its position on a map.


### Based on

- [Google Maps](https://maps.google.com/)
- [gmaps.js](https://hpneo.github.io/gmaps/)
- [requirejs-plugins/async](https://github.com/millermedeiros/requirejs-plugins)
- [org.apache.cordova.geolocation](https://github.com/apache/cordova-plugin-geolocation)