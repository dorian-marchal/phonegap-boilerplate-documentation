# Build the app for distribution

### dist file

To reduce the start-up time and the app size, you can build a distribution app file.
This file (`www/dist/main.js`) is a compilation of all the app files.

This file is produced by __r.js__, the RequireJS optimizer.
The configuration file of the optimizer is `www/build.js`.

You can refer to the [r.js documentation](http://requirejs.org/docs/optimization.html),
for more informations.

### Build

When you want to build a ditribution version of your app :

1. Change the `environment` variable value in `www/index.html`, from `dev` to `dist`
2. Rebuild your app with `make build`
