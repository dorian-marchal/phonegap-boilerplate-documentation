# Global





* * *

## Class: Loader
Helper used to add a Spin.js loader to an element.

### Loader.Loader($el, options) 

Create a new loader.

**Parameters**

**$el**: `$`, jQuery or DOM element in which the loader will be added

**options**: `string | object`, Whether :
    - {string} : A preset name previously added with addPreset (or Spin.js
                 options object)
    - {object} : Additional Spin.js options object


### Loader.addPreset(name, preset) 

*Static function*
Add a preset of options. All presets inherit the default one
So the option properties are not all required.
The default preset can be overriden.

**Parameters**

**name**: `String`, Name of the preset

**preset**: `Object`, The preset to add


### Loader.start() 

Add the spinner to the spinner element


### Loader.stop() 

Remove the spinner from the DOM




* * *










