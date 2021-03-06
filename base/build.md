# Build the app for distribution

### Version number

In Phonegap Boilerplate server, you can set the version number in `./version.json`.
When a server is running, you can get its version by calling the route `GET /version`.

### Dist file

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

To make requirejs use your compiled file, change the `window.useDistFile` variable to `true`.

__Note:__ If `isProductionConfig` or `window.useDistFile` are `false`, a warning will be displayed.

![toast](https://cloud.githubusercontent.com/assets/6225979/8487822/c79f1d60-210e-11e5-9747-1b882a1d6418.png)

This helps to avoid pushing a dev app on a store (as I once did... :no_mouth:).

To disable this warning, set the `hideDistWarning` to `true` in your config file.
