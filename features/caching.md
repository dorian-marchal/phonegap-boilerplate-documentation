# Server API Caching

You can easily cache your API requests with the apicache middleware available as
`RestServer.apicache`.

### Usage

```js
server.app.get('/hello-world', server.apicache(), function (req, res) {
    res.send('Hello World !');
});
```

### Configuration

`cache.disable`: `true` if you want to disable caching, defaults to `false`.
`cache.duration`: caching duration in milliseconds (2 hours by default -> 3600000)


### Based on

- [apicache](https://github.com/kwhitley/apicache)
