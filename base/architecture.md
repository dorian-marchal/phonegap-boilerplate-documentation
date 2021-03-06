# Overall architecture

## Directory Tree

The app webroot is `www` :

```
www
 |
 |- css/        Compiled css files
 |  |- fonts/      Font files
 |  |- lib/        CSS libraries
 |  `- sass/       SCSS files (compiled to CSS files)
 |
 |- dist/
 |  `- main.js     Compiled app for distribution
 |
 |- js/
 |  |- app/        Application specific js files
 |  |- core/       Core js files
 |  |- lib/        js third party libraries
 |  |- app.js      App main
 |  |- config.js   App config
 |  `- core.js     App core
 |
 |- locales/    Internationalization files (see  'Internationalization')
 |
 |- res/        Icon and splashscreen source (see 'Generating an icon/splashscreen')
 |
 `- spec/       Phonegap test suit
```

## App loading scenario

### 1. Index loading

The index, `www/index.html`, is loaded. The `useDistFile` variable determines the first loaded file :

- When `false`, `www/js/app.js` is loaded.

- In production, the `useDistFile` variable must be set to `true`, and `www/dist/main.js` is loaded (a compilation of all files, for a faster start-up).

### 2. App start-up (`www/js/app.js`)

This file is an entry point responsible for setting up the app architecture.

__It goes like this :__

- Config loading ([↓ see config details](#config-details))
- Cordova loading ([↓ more informations](#cordova-mocking))
- Language initialization (from device)
- [↓ before init hook](#before-init-hook)
- [↓ init hook](#init-hook)
- Authentication checking ([Go to the authentication doc ↱](auth.md))
- Create the `globals` singleton ([See globals documentation  ↱](globals.md))
- Router creation ([Go to the routing doc ↱](routing.md))
- App start-up : `js/app/router.js`

### 3. First page loading

The router (`js/app/router.js`) determines the page to load based on the current url `#hash`.  
The routing logic can be found [here ↱](routing.md) (you can also read the [router configuration ↱](router.md))

---

## More informations

### Config details

The configuration of an app is based on three files, loaded in the following order (The last can override the previous one, wich can override the first one) :

- `www/js/core/core-require-conf.js` : The configuration file of Phonegap Boilerplate. This file must not be edited.
- `www/js/core.js` : The core file of your app. It is used to adjust Phonegap Boilerplate to your needs and alias your dependencies.
- `www/js/app/config.js` : Your app configuration variables go in there. This file is not checked in version control.

These files are mixed together. The app config is accessible via the `config` property of the `globals` module.

Exemple :
```js
define(['globals'], function (globals) {
    console.log(globals.config.appName); // Log the app name
});
```

### Cordova mocking

When the app is loaded in the browser, the Cordova API is not available.
To enable testing in the browser, a fake `cordova.js` file is loaded. This file
mock the Cordova API and plugins.

### Before init hook

The `beforeInitHook` (`www/js/app/initHook.js`) is called just before initializing
you app router, views, models, dependencies, ...
A use case for this hook is editing the configuration before loading your app modules.

For example, the `gmaps` dependency can only be resolve with an internet connection.
In this case, you may want to add some code in the `beforeInitHook` to warn your users
when there is no available connection.

`beforeInitHook` is asynchronous, so you must call its callback when you're done :

```js
return function (done) {

    // Code executed before init
    // ...

    done();
};
```

### Init hook

If you want to add some code that will be executed before the app start, but
after your app modules are loaded, you can add it in `www/js/app/initHook.js`.
The function returned by this module is called before the splashscreen is hidden.

`initHook` is asynchronous, so you must call its callback when you're done :

```js
return function (done) {

    // Code executed at start-up
    // ...

    done();
};
```
