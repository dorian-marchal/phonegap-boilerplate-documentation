# Global





* * *

## Class: UserLocationTracker
Helps to add a marker that follow the user on a map. Extends backbone.Event.
This helper trigger an 'firstPositioning' event when the first location is found
after tracking start with two parameters : the map and the new position

### UserLocationTracker.setMap(map) 

Set the tracker map

**Parameters**

**map**: `Gmaps`, Gmaps instance


### UserLocationTracker.setMarkerIconOptions(iconOptions) 

Update the marker icon options

**Parameters**

**iconOptions**: `Object`, google.maps.marker options


### UserLocationTracker.start() 

Start showing the user position on the map.

**Fires**: event:firstPositioning When the first position is found


### UserLocationTracker.stop() 

Stop showing the user position.
Be careful, this does not stop tracking the geolocation.




* * *










