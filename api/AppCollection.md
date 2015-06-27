# Global





* * *

## Class: AppCollection
A base collection.
All the app collections must inherit from this.
The general code of the collections goes here.

Example :

```js
define([
    'core/models/AppCollection',
    'app/models/Deal'
], function(AppCollection, Deal) {
    'use strict';

    return AppCollection.extend({
        route: '/deals',
        model: Deal,
    });
});
```

**route**: `String` , The API route
**model**: `AppModel` , Model in the collection


* * *










