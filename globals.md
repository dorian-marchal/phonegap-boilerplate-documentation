# `globals` singleton

The `globals` module (`app/singletons/globals`) is a singleton where all the global app data are stored.
It was added mainly to avoid circular dependencies (with objects like app router).

### - `globals.config`

Application configuration (merge of `app/config.js`, `app/core.js` and `core/core-require-conf.js`)

### - `globals.currentPage`

The `AppPage` instance currently displayed. This global property is updated when
a new page is slided in (between the `AppPage.afterRender` and the `AppPage.afterLoad` hooks).

### - `globals.router`

`Backbone.Router` of the application.

### - `globals.route`

Current route params (`controller`, `action` and `params`).
