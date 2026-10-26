# The Crew

A source plugin for [Playpex Media Server](https://github.com/IhebBelhadj/Playpex): a port of the Kodi add-on The Crew (GPL-3.0) to a Playpex plugin, keeping its sources that still work and its debrid services.

| Part | Gives | Default |
|---|---|---|
| Torrentio | a title's torrents from many sites, by IMDb id (an episode's own file, also inside season packs) | on |
| Knaben | a search across torrent sites, with live seed counts | on |
| Real-Debrid, AllDebrid | a torrent you pick, played as a direct stream when the service has it (asked when you pick it: they no longer say what they have) | your API token / key |
| Premiumize, TorBox | the torrents they have marked "Cached on …" and played at once as direct streams | your API key |

Its sources show in a title's **Play**, in the dashboard's **Search** and in **Find releases**. Sources are switches and accounts are entered in the plugin's settings (dashboard › Plugins › The Crew › Settings; "Check the accounts" tests them). The plugin asks only for these services' hosts, the account keys you enter, and for direct files and magnet sources. Needs a Playpex server with the `tries` answer of `play.resolve` (Real-Debrid and AllDebrid are only tried on servers that have it).

## Add it to a server

On the server's dashboard: **Plugins › Repositories › Add repository**, then

```
https://ihebbelhadj.github.io/playpex-thecrew/index.json
```

Check that the key fingerprint shown is `e371 0e2c 23b9 8ef3 b5f0 af83 7f72 05c7`, then **Trust and add**, and install The Crew from **Browse**.

Without the repository: trust the publisher key `ed25519:chBAohkJROLT7ApepFY09WUFh5QbHpAuheHPukXB/XE=` under **Plugins** (trusted publisher keys) and upload the `.ppx` file: the package is signed with it too.

## What is here

The repository's signed index (`index.json`, its signature `index.json.sig`) and the package it lists, built from `plugins/thecrew/` of the Playpex repository with

```
npm run pack:repository -- plugins/thecrew \
  --out ../playpex-plugins/thecrew --key ../playpex-keys/thecrew.json --id thecrew --name "The Crew" \
  --base-url https://ihebbelhadj.github.io/playpex-thecrew/ --sign-packages
```

Servers check the index against the key they trusted, and the package against its sha256. Use the same key for every new version (raise the plugin's `version` first): servers that trusted it refuse an index signed by another.

## License and note

The plugin is GPL-3.0, like The Crew it derives from (its `LICENSE` is inside the package). An educational project: streaming copyrighted content may be illegal where you live.
