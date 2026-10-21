# Dragonfly

## From their [GitHub](https://github.com/dragonflydb/dragonfly)

Dragonfly is an in-memory data store built for modern application workloads. It is fully compatible with Redis and Memcached APIs and requires no code changes to adopt.

## Dragonfly Version

The installer downloads the official Dragonfly binary from the [GitHub releases](https://github.com/dragonflydb/dragonfly/releases) (x86_64 or aarch64).
The version is set with the `Dragonfly Version` variable (`1.27.1` by default, or `latest`). Reinstall the server to change it, your data is kept.

The server runs on the `ghcr.io/parkervcp/yolks:redis_8` image, which provides `redis-cli` for the console.
The exact version is printed in the console on every start (`dragonfly_version:...`).

## Server Startup

You must first authenticate before trying to execute commands, to do this run `AUTH <YOUR_PASSWORD_HERE>` (without the `<>`). This should be the same as the password set in the `SERVER_PASSWORD` variable.

The server is marked as started once Dragonfly answers a `PING`, so it only shows as running when it is ready to accept connections.

## Memory and Threads

Dragonfly needs at least 256 MB of memory per thread. The `Threads` variable defaults to `1`, raise it together with the server memory.
Setting it to `0` uses every CPU core of the host, which usually needs more memory than the server has.

## Persistence

Data is saved to `/home/container` as `dump-*.dfs` files on shutdown and on the `Snapshot Schedule` cron (every 5 minutes by default).

## Server Ports

Ports required to run the server in a table format.

| Port    | default |
|---------|---------|
| Server  |  6379   |
