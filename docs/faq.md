# FAQs

## How does the network scanning work?

The optional discovery mode is [scanning](https://linux.die.net/man/1/arp-scan>)
a configured network interface for all devices and tries to call the common HTTP(S) ports to discover
a known 3D printer service such as OctoPrint. If it finds one, it adds it
automatically to Karmen. This feature is not available in the cloud mode.

## How can I add a password protected Octoprint?

OctoPrint's protected instances can be communicated with by using an API token
that you can add to each printer on its settings screen. See [Connecting
OctoPrint
section](connection-your-devices.md?id=connecting-octoprint-enabled-devices) for
further information.

## Can I run more Karmen instances on a single machine?

Yes, you can. The `docker-compose.yml` file can be parametrized by a few
environment variables and you can reconfigure all of the things needed to
create multiple instances of Karmen Hub next to each other.

You need to configure an isolated disk space for gcodes and for the database and
you need to pick free ports for all the services.

This setup is not ideal though, as all of the instances are run by the same system users
and might share some defaults such as database password. This might change in the future.

```bash
KARMEN_FILES_DIR=./k2-files \
KARMEN_DB_DIR=./k2-pg-datadir \
KARMEN_POSTGRES_PORT=5434 \
KARMEN_REDIS_PORT=6380 \
KARMEN_BACKEND_PORT=9800 \
KARMEN_FRONTEND_PORT=9801 \
KARMEN_PORT=8081 \
    docker-compose up
```
