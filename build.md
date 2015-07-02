# Build the app for distribution

### dist file

To reduce the start-up time and the app size, you can build a distribution app file.
This file (`www/dist/main.js`) is a compilation of all the app files.

This file is produced by __r.js__, the RequireJS optimizer.
The configuration file of the optimizer is `www/build.js`.

You can refer to the [r.js documentation](http://requirejs.org/docs/optimization.html),
for more informations.

### Build

When you want to build a distribution version of your app,

1. Set the `isProductionConfig` to `true` in your config file (`www/js/config.js`)
2. Rebuild your app with `make build`

### Configuration

To make requirejs use your compiled file, change the `window.environment` variable value
in `www/index.html`, from `"dev"` to `"dist"`.

__Note:__ If `isProductionConfig` is `false` or `window.environment` isn't set to `"dev"`, a warning will be displayed.

This helps to avoid pushing a dev app on a store (as I once did... :no_mouth:).

To disable this warning, set the `hideDistWarning` to `true` in your config file.
