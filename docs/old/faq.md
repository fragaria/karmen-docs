# FAQs

## Which devices are supported?

Karmen is compatible with all printers OctoPrint is compatible with. That means
it is compatible with **most of available consumer 3D printers**. Should you
have any trouble making it work with your device, just ping us using any channel
mentioned [here](/?id=getting-help).

## How does the network scanning work?

Auto discovery uses the arp-scan. See more info in the
[printers](old/printers.md?id=automatic-printer-discovery) section.

## How can I add a password protected OctoPrint?

OctoPrint's protected instances can be communicated with by using an API token
that you can add to each printer on its settings screen. See [Using OctoPrint
access control](old/printers.md?id=using-octoprint-access-control) entry for further
information.

## Can I run more Karmen instances on a single machine?

Yes, you can. The `docker-compose.yml` file can be parametrized by a few
environment variables and you can reconfigure all of the things needed to
create multiple instances of Karmen Hub next to each other.

You need to configure an isolated disk space for G-codes and for the database and
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
