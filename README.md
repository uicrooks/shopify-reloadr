## Shopify Reloadr

> This package is now deprecated, consider using [Shopify Theme Lab Reloader](https://github.com/uicrooks/shopify-theme-lab-plugins/tree/master/packages/reloader)

Shopify Reloadr is a collection of scripts for reloading a remote Shopify theme during development when working with [Shopify Theme Lab](https://github.com/uicrooks/shopify-theme-lab).

The `server.js` script runs an HTTP server, as well as a WebSocket server, locally. The HTTP server listens for requests, sent from the `shopify:watch` task (which is the default Shopify Them Kit [watch task](https://shopify.dev/tools/theme-kit/command-reference#watch)) and communicates via WebSocket connection with the `client.js` script.

The `client.js` script (WebSocket client) is injected into the webpack bundle, during development, and connects via `localhost:port` to the WebSocket server. The script listens to reload messages from the server script.

If the connection between `client.js` and `server.js` is lost, `client.js` tries every couple of seconds to reconnect to the server.

Settings and ports for the script can be adjusted in `package.json`.

## Settings
| Option | Description |
| - | - |
| serverPort | the localhost port `shopify:watch` task and `server.js` use to communicate |
| websocketPort | the localhost port `server.js` and `client.js` use to communicate |
| delay | auto-reload needs a slight delay before reloading the remote site, so all newly uploaded files will be loaded. Values between `1600`ms and `2000`ms seem to work well |