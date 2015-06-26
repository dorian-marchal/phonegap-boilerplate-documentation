# Global





* * *

## Class: GeolocationHelper
Helper to easily add global geolocation to an app via
navigator.geolocation (Phonegap).

### GeolocationHelper.getDistanceBetween(pointA, pointB) 

Static function that calculate the distance between two points on Earth

**Parameters**

**pointA**: `object`, {latitude, longitude}

**pointB**: `object`, {latitude, longitude}

**Returns**: `int`, distance in meters

### GeolocationHelper.getCurrentPosition(options) 

Get the current GPS coordinates

**Parameters**

**options**: `object`, Same options as `navigator.geolocation.watchPosition`

**Fires**: locationSuccess when a location is found (a Position object is passed)

**Fires**: currentPositionSuccess when a location is found (a Position object is passed)

**Fires**: locationError when an error occur (an Error object is passed)

**Fires**: currentPositionError when an error occur (an Error object is passed)


### GeolocationHelper.startTracking() 

Start the tracking

**Fires**: event:trackingStart


### GeolocationHelper.stopTracking() 

Stop the tracking

**Fires**: event:trackingStop


### GeolocationHelper.toggleTracking() 

Toggle the geolocation tracking

**Fires**: event:trackingStart if the tracking has been started

**Fires**: event:trackingStop if the tracking has been stopped

**Returns**: `Boolean`, true if the tracking has been started, false otherwise

### GeolocationHelper.isTracking() 

Helper to easily add global geolocation to an app via
navigator.geolocation (Phonegap).

**Returns**: `Boolean`, true if the tracking is started, false otherwise

### GeolocationHelper.getLastPosition() 

Helper to easily add global geolocation to an app via
navigator.geolocation (Phonegap).

**Returns**: `Position`, the last known position



* * *










