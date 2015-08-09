# Miscellaneous

### Force a route at app start

To force the first loaded page in your app, add this line in your config file (`www/config.js`) :

```js
    firstLoadedRoute: '/my-route/with/parameters',
```

### Dial a number from app

To make a link that dial a number, use the `tel:` pseudo-protocol :

```html
<a href="tel:XXXXXXXX" >Dial a number</a>
```

In order to make this link work, you must allow it on `config.xml` :

```xml
<access origin="tel:*" launch-external="yes" />
```

The process is the same for the `mailto:` pseudo-protocol

```xml
<access origin="mailto:*" launch-external="yes" />
```
