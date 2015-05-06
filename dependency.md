# Add a dependency to your app

Your app dependencies must be stored in `/www/js/lib`.

Usually, dependencies are fetched with bower (in `/bower_components`) and added to the libs on build.

Currently, the build is performed with `make build`.

For example, Backbone is added in `/www/js/lib` with this line in the Makefile :

```
cp bower_components/backbone/backbone.js www/js/lib/
```

This way, the whole `backbone` directory is not added to the assets in the built apps.

To add your own dependency, simply add it at the end of the Makefile.

You can then configure the require `path` (and optionnaly `shim`) in `js/core.js` (see `js/core/core-require-conf.js` for an example).
