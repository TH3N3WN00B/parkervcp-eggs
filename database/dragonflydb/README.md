# Dragonfly

## From their [GitHub](https://github.com/dragonflydb/dragonfly)

Dragonfly is an in-memory data store built for modern application workloads. It is fully compatible with Redis and Memcached APIs and requires no code changes to adopt.

## Dragonfly Version

The installer downloads the official Dragonfly binary from the [GitHub releases](https://github.com/dragonflydb/dragonfly/releases) (x86_64 or aarch64).
The version is set with the `Dragonfly Version` variable (`2.0.2` by default, or `latest`). Reinstall the server to change it, your data is kept.

The server runs on the `ghcr.io/parkervcp/yolks:redis_8` image, which provides `redis-cli` for the console.
The exact version is printed in the console on every start (`dragonfly_version:...`).

## Server Startup

The console is already authenticated with the password set in the `SERVER_PASSWORD` variable, so commands such as `SAVE` or `INFO` can be run directly.

The server is marked as started once Dragonfly answers a `PING`, so it only shows as running when it is ready to accept connections.

## Memory and Threads

Dragonfly needs at least 256 MB of memory per thread. The `Threads` variable defaults to `1`, raise it together with the server memory.
Setting it to `0` uses every CPU core of the host, which usually needs more memory than the server has.

## Persistence

Data is saved to `/home/container` as `dump-*.dfs` files on shutdown and on the `Snapshot Schedule` cron (every 5 minutes by default).

## Importing data from Redis

Switch a Redis server to this egg and reinstall it. No other step is needed:

* The installer copies the Redis `dump.rdb` to `backups/<date>-redis-<version>/`.
* Dragonfly imports `dump.rdb` on its first start. From then on it saves and loads its own `dump-*.dfs` files, and the old `dump.rdb` is no longer used.
* This was tested with data written by Redis 5.0, 6.2, 7.4 and 8.2 (strings, hashes, lists, sets, sorted sets, TTLs and several databases). Data from Redis modules, or types that only exist in newer Redis versions, may not be supported by Dragonfly.

Going back to Redis is not automatic, because Dragonfly saves in its own format. To return to Redis with the original data, stop the server and copy `dump.rdb` back from `backups/`.

## Server Ports

Ports required to run the server in a table format.

| Port    | default |
|---------|---------|
| Server  |  6379   |
