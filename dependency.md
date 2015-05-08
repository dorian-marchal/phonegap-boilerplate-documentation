# Add a dependency to your app

Your app dependencies must be stored in `/www/js/lib` (js) and `/www/css/lib` (css).

### Bower

Usually, dependencies are fetched with bower (in `/bower_components`) and added
to the libs on build.

For exemple, backbone is fetched with this command :

```bash
bower install --save backbone
```

Note that bower components are checked in git.

### Build

Currently, the build is performed with `make build`.

For example, Backbone is added in `/www/js/lib` with this command in the Makefile :

```
cp bower_components/backbone/backbone.js www/js/lib/
```

This way, the whole `backbone` directory isn't added to the assets of the built
apps.

To add your own dependency, simply add it to the `build-app-dependencies` rule in
the Makefile.

### Require

You can then configure the require `path` (and optionnaly `shim`) in `js/core.js`
(see `js/core/core-require-conf.js` for an example).
You'll need to add your dependencies in `www/build.js`, too, if you want them to
be found by r.js.
