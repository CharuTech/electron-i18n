# Commandes Chromes Supportées

> Les paramètres de ligne de commande pris en charge par Electron.

Vous pouvez utiliser [app.commandLine.appendSwitch](app.md#appcommandlineappendswitchswitch-value) pour ajouter à votre script principal de votre application avant que l'événement [ready](app.md#event-ready) du module [app](app.md) soit émis :

```javascript
const {app} = require('electron')
app.commandLine.appendSwitch('remote-debugging-port', '8315')
app.commandLine.appendSwitch('host-rules', 'MAP * 127.0.0.1')
app.on('ready', () => {
  // Votre code ici
})
```

## --ignore-connections-limit=`domains`

Ignore la limite de connexion pour la liste de `domains` séparés par `,`.

## --disable-http-cache

Désactive le cache disque pour les requêtes HTTP.

## --disable-http2

Désactive les protocoles HTTP/2 et SPDY/3.1.

## --inspect=`port` et --inspect-brk=`port`

Les indicateurs relatifs au débogage, reportez-vous au guide [Déboguer le processus principal](../tutorial/debugging-main-process.md) pour plus de détails.

## --remote-debugging-port=`port`

Active le débogage distant via HTTP sur le `port` spécifié.

## --disk-cache-size=`size`

Force l'espace disque maximum à utiliser par le cache disque, en octets.

## --js-flags=`flags`

Spécifie les indicateurs a transmettre au moteur de NodeJS. Il doit être indiqué lors du démarrage d'Electron si vous souhaitez activer les `flags` dans le processus principal.

```bash
$ electron --js-flags="--harmony_proxies --harmony_collections" votre-app
```

Voir la [documentation de Node](https://nodejs.org/api/cli.html) ou exécutez `node --help` dans votre console pour avoir la liste des indicateurs disponibles. De plus, exécutez `node --v8-options` pour afficher la liste des indicateurs qui se réfèrent spécifiquement au moteur JavaScript V8 de Node.

## --proxy-server=`address:port`

Utiliser le serveur proxy spécifié, qui remplace le paramètre système. Cet indicateur n'affecte que les requêtes avec le protocole HTTP, y compris les requêtes HTTPS et WebSocket. Il est également intéressant de noter que tous les serveurs proxy ne supportent pas les requêtes HTTPS et WebSocket.

## --proxy-bypass-list=`hosts`

Demande à Electron de contourner le serveur proxy pour la liste d'hôtes séparées par des semi-colons. Cet indicateurs prend effet uniquement si utilisé conjointement avec `--proxy-server`.

Par exemple :

```javascript
const {app} = require('electron')
app.commandLine.appendSwitch('proxy-bypass-list', '<local>;*.google.com;*foo.com;1.2.3.4:5678')
```

Will use the proxy server for all hosts except for local addresses (`localhost`, `127.0.0.1` etc.), `google.com` subdomains, hosts that contain the suffix `foo.com` and anything at `1.2.3.4:5678`.

## --proxy-pac-url=`url`

Uses the PAC script at the specified `url`.

## --no-proxy-server

Don't use a proxy server and always make direct connections. Overrides any other proxy server flags that are passed.

## --host-rules=`rules`

A comma-separated list of `rules` that control how hostnames are mapped.

Par exemple :

* `MAP * 127.0.0.1` Forces all hostnames to be mapped to 127.0.0.1
* `MAP *.google.com proxy` Forces all google.com subdomains to be resolved to "proxy".
* `MAP test.com [::1]:77` Forces "test.com" to resolve to IPv6 loopback. Will also force the port of the resulting socket address to be 77.
* `MAP * baz, EXCLUDE www.google.com` Remaps everything to "baz", except for "www.google.com".

These mappings apply to the endpoint host in a net request (the TCP connect and host resolver in a direct connection, and the `CONNECT` in an HTTP proxy connection, and the endpoint host in a `SOCKS` proxy connection).

## --host-resolver-rules=`rules`

Like `--host-rules` but these `rules` only apply to the host resolver.

## --auth-server-whitelist=`url`

A comma-separated list of servers for which integrated authentication is enabled.

Par exemple :

    --auth-server-whitelist='*example.com, *foobar.com, *baz'
    

then any `url` ending with `example.com`, `foobar.com`, `baz` will be considered for integrated authentication. Without `*` prefix the url has to match exactly.

## --auth-negotiate-delegate-whitelist=`url`

A comma-separated list of servers for which delegation of user credentials is required. Without `*` prefix the url has to match exactly.

## --ignore-certificate-errors

Ignores certificate related errors.

## --ppapi-flash-path=`path`

Sets the `path` of the pepper flash plugin.

## --ppapi-flash-version=`version`

Sets the `version` of the pepper flash plugin.

## --log-net-log=`path`

Enables net log events to be saved and writes them to `path`.

## --disable-renderer-backgrounding

Prevents Chromium from lowering the priority of invisible pages' renderer processes.

This flag is global to all renderer processes, if you only want to disable throttling in one window, you can take the hack of [playing silent audio](https://github.com/atom/atom/pull/9485/files).

## --enable-logging

Prints Chromium's logging into console.

This switch can not be used in `app.commandLine.appendSwitch` since it is parsed earlier than user's app is loaded, but you can set the `ELECTRON_ENABLE_LOGGING` environment variable to achieve the same effect.

## --v=`log_level`

Gives the default maximal active V-logging level; 0 is the default. Normally positive values are used for V-logging levels.

This switch only works when `--enable-logging` is also passed.

## --vmodule=`pattern`

Gives the per-module maximal V-logging levels to override the value given by `--v`. E.g. `my_module=2,foo*=3` would change the logging level for all code in source files `my_module.*` and `foo*.*`.

Any pattern containing a forward or backward slash will be tested against the whole pathname and not just the module. E.g. `*/foo/bar/*=2` would change the logging level for all code in the source files under a `foo/bar` directory.

This switch only works when `--enable-logging` is also passed.