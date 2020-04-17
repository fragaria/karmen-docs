# Installing Karmen on-premise

## Installation

Karmen should run on any OS supporting [Docker](https://www.docker.com) running on ``amd64`` or ``arm/v7`` architecture.
We recommend using a standalone computer for it. Specifically, a [Raspberry Pi 4](https://www.raspberrypi.org) is a great fit.
Docker can be easily installed on Raspberry Pi by running a few commands adapted from this
[official blogpost](https://blog.docker.com/2019/03/happy-pi-day-docker-raspberry-pi/).
We recommend using a clean Raspbian image as a base for installing Karmen.

If you use a freshly installed Raspbian image, make sure that you run `sudo apt update && sudo apt upgrade -y && sudo reboot`
before installing Docker. That updates the system to the latest version and performs a restart.

### Install Docker

```bash
sudo apt install software-properties-common -y
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
sudo usermod -aG docker pi
sudo apt install docker-compose -y
sudo reboot
docker info # should print out some docker engine information
```

### Get Karmen bundle

The next step is to get Karmen production bundle. You will find the latest
release on the [GitHub releases
page](https://github.com/fragaria/karmen/releases). Or you can just copy-paste
following code snippet to achieve the same result:

```bash
cd
wget -O karmen.zip https://github.com/fragaria/karmen/releases/latest/download/release.zip
unzip karmen.zip
cd karmen
```

The directory `karmen` now contains at least the following files:

- `docker-compose.yml` - A blueprint for all the necessary services
- `run-karmen.sh` - A startup script you can use to launch Karmen
- `stop-karmen.sh` - A script you can use to stop Karmen
- `update.sh` - An update script that can bring your installation up to date
- `VERSION` - A file with a version number useful for troubleshooting

The database schema is created automatically upon the first start and is kept up
to date during updates. The datafiles are created on your filesystem, not inside
the container, so no data will be lost during Karmen's downtime.

Karmen needs to be [configured](on-premise.md?id=configuration) before first
launch. It is done exclusively with [environment
variables](https://en.wikipedia.org/wiki/Environment_variable). The only
required one is `KARMEN_SECRET_KEY` which you should set to something secret and
never share with anyone. It is used for session encryption and should be unique
for each installation.

Another important environment variable is the `KARMEN_CLOUD_MODE`. If it is set to
`0`, Karmen will try to work with Karmen Pills, OctoPrints and printers
available directly over the network. If it is set to `1`, the application
presumes that it is running somewhere on the internet and the devices are
connected over a specialized [websocket
proxy](https://github.com/fragaria/websocket-proxy) that comes preconfigured on
Karmen Pill. When you are setting `KARMEN_CLOUD_MODE` to `1`, you also need to
provide `KARMEN_SOCKET_API_URL` variable which points to the websocket proxy
instance.

If you want to allow user registration, you need to configure a mailing service
as well. Consult the [configuration](on-premise.md?id=configuration) section for
more information.

Finally, you can start all of the services. During the first startup, the script
will automatically download and run all of the necessary containers from [Docker
Hub](https://hub.docker.com/search?q=fragaria%2Fkarmen&type=image>). This might
take a few minutes. For the first and all other starts, you can use the
shorthand script like this:

```bash
KARMEN_CLOUD_MODE=0 KARMEN_SECRET_KEY=[secret key] ./run-karmen.sh
```

Once command finishes, a browser-accessible frontend app will be available on
the standard HTTP port 80. Again, consult the
[configuration](on-premise.md?id=configuration) section for more configruation
options including the used ports.

You can see the UI by accessing the public IP address of your machine, or by visiting the
`<hostname>.local` address which is automatically provided by Raspbian. The default hostname
for standard Raspbian is `raspberrypi` and can be changed from the command line by running the
`raspi-config` program.

!> Raspbian and OctoPi provide the `<hostname>.local` service via
[mDNS](https://en.wikipedia.org/wiki/Multicast_DNS). This technology might not
work on some clients without further configuration.

You can stop everything by running

```shell
./stop-karmen.sh
```

You probably want to start Karmen every time your Raspberry Pi boots up.
Arguably the easiest (but in no way perfect) method is to add the following line
at the end of your `/etc/rc.local` file just before the `exit 0` line:

```
KARMEN_CLOUD_MODE=0 KARMEN_SECRET_KEY=[secret key] /home/pi/karmen/run-karmen.sh >> /home/pi/karmen/startup.log
```

This will also put all of the startup information into a logfile in case you
need to debug when something doesn't work as expected. Be aware that this method
starts all of the containers under the `root` account, which might not be the best
idea. A better option might be a
[systemd](https://www.linode.com/docs/quick-answers/linux/start-service-at-boot/)
service which can be configured with a file like this:

```ini
[Unit]
Description=Karmen
DefaultDependencies=no
After=docker.service

[Service]
Environment="KARMEN_CLOUD_MODE=0"
Environment="KARMEN_SECRET_KEY=something-secr3t"
Environment="KARMEN_HOST=127.0.0.1"
Environment="KARMEN_PORT=3776"
User=pi
Group=users
ExecStart=/usr/bin/karmen
RemainAfterExit=yes
ExecStop=/usr/bin/karmen-stop

[Install]
WantedBy=multi-user.target
```

`/usr/bin/` scripts are just links to the aforementioned `run-karmen.sh` and `stop-karmen.sh` scripts.

You should also keep your installation up-to-date at all times. There is
[dedicated docs section](on-premise.md?id=updating) on this topic.

### Configuring user access

Upon installation, there is an administrator account ready with username `karmen` and
password `karmen3D` for you. The application will prompt you to change the password upon
the first login.

!> Make sure that you log in right after the installation is complete so nobody
else can hijack the installation from you.

There is also a *Default organization* ready for you. You can rename it at any
time. As an administrator, you can invite more users to your organization. That
requires a working mailing service. See
[configuration](on-premise.md?id=configuration) section to learn how to
configure it.

Also, for some actions, such as another password change or adding users, you
need to re-authenticate with your password from time to time. Don't be
alarmed if the application prompts for your password again.

For more information about users and organizations, see [Managing access &
organizations docs](access.md).

## Updating

Every software needs to be updated over time to get new functionality or just
to fix some existing issues. Because Karmen is distributed as a bunch of Docker images,
updating is rather simple.

### Getting the latest release

All new releases show up in [the releases section](https://github.com/fragaria/karmen/releases>)
on our GitHub. You can get notifications if you start watching the repository or you can subscribe
to the [Atom feed](https://github.com/fragaria/karmen/releases.atom). Any major changes will also
probably be announced on our social media.

### Using the update script

We have prepared an update script that can perform all of the steps for you.
**However, it doesn't hurt to always have a manual backup before running an
automated update.**

If you've followed the [installation guide](on-premise.md?id=installation), you
should have the `karmen` directory in Raspberry Pi's home directory of `/home/pi`.
There should also be the `update.sh` script. It does all the steps described
below for you and after running it, you should be ready to start Karmen again
from a new version either by restarting your device (if you have set up the
startup script), or by running

```shell
<YOUR CONFIGURATION ENVVARS> /home/pi/karmen/run-karmen.sh
```

By default, the update script will update to the latest stable release. If
you're feeling adventurous, you may update to an unstable release by running
`update.sh --edge`.

### Updating manually

All of the following commands are run from the `/home/pi/karmen` directory unless stated otherwise.

1. Stop Karmen with `./stop-karmen.sh`.
2. Do a backup of the whole `karmen` directory including the PotsgreSQL datafiles.
3. Get the latest (or specific) `release.zip` from GitHub and unpack its contents into the `karmen` directory.
4. Run `docker-compose pull` to get the latest versions of docker containers.
5. Start Karmen again with

```shell
<YOUR CONFIGURATION ENVVARS> /home/pi/karmen/run-karmen.sh
```

## Exposing your installation to the Internet

Karmen is successfully running in your environment, but to make the whole system
really useful, there is still one thing missing: *the ability to manage your
printers when you're outside of your local network*. There are multiple ways of
doing that, take the following list as an inspiration on how it can be done.

### Using Karmen Pill and Karmen SaaS

To most straightforward solution is to get our [Karmen
Pill](pill-getting-started.md) and register it with our cloud service. Follow
the [docs guide](pill-getting-started.md) to get started. You can [order your
Pill online](https://karmen.tech) on our website.

### Deployment accessible from the internet

This is the obvious choice. You can run Karmen on a server accessible from the
internet easily. The more difficult bit is to make your OctoPrint also available
over the internet. Don't forget to protect all of your services that are
publicly accessible with passwords and TLS.

#### Websocket proxy

You can use our [websocket-proxy](https://github.com/fragaria/websocket-proxy)
that is supported in Karmen out of the box with `KARMEN_SOCKET_API_URL` and
`KARMEN_CLOUD_MODE` options. It requires a client running next to your OctoPrint
and a server running in a location accessible by Karmen. The communication is
secured and encrypted

#### Port mapping on a router

If you have your service set up behind a router with a fixed public IP address,
you can use the [port mapping (or port
forwarding)](https://en.wikipedia.org/wiki/Port_forwarding) technique. Just pick
a port number and set up a [route on your
router](https://portforward.com/router.htm>) that maps an outgoing port to the
internal device's address.

**An example:** Your public IP is `1.2.3.4`, Karmen is running locally on
`192.168.3.89` and you pick an external port `44444`. After setting things up
properly, Karmen will be available on `1.2.3.4:44444`. All traffic including the
webcam streams is now routed to the internet through this mapped port.

!> This solution is **not safe** out-the-box since the traffic is not encrypted. You should
protect the outgoing service with a TLS certificate by all means.

#### Virtual Private Network (VPN)

Some routers offer a simple way of creating a VPN, basically a tunnel that makes your local
network accessible via a secured connection from anywhere in the world. This solution is better
than simple port mapping, because it uses an encrypted communication channel by definition.

If your router does not support VPN, you can get away with other solutions, such as
[PiVPN](http://www.pivpn.io/). VPN also makes all of your printers available directly,
so the webcam streams might be a little smoother.

#### SSH tunneling

If you have no control over the network element that provides the internet access or you
cannot simply run or get a VPN, [SSH tunneling](https://www.ssh.com/ssh/tunneling/)
is yet another option that can be used.

In short, you open an SSH tunnel from the computer that is running the service
to a computer that is visible from the internet. A part of that tunnel is again
a port mapping. So let's say that Karmen is running on `192.168.3.89:80` and
your internet-visible computer is `1.2.3.4`. You can then open a tunnel by
running following command in shell:

```shell
ssh -R 8888:localhost:80 1.2.3.4
```

By running that command, you are routing Karmen local port `80` to
`1.2.3.4:8888`. So anybody that can access `1.2.3.4:8888` can now access Karmen,
too. In this situation, the traffic between `1.2.3.4` and Karmen is encrypted.
The traffic between the end user and `1.2.3.4` is not however, unless the public
facing computer is configured to use a TLS certificate.

#### Online tunneling services

There are some online services such as [ngrok](https://ngrok.com/) that can
establish a publicly accessible tunnel to your computer. These are usually great
for a temporary or testing setup, but for a permanent solution, other approaches
tend to be better.

## Configuration

If you are running Karmen in the [recommended
way](on-premise.md?id=installation), you can adjust the software's behaviour by
various environment variables.

These are interpreted in the `docker-compose.yml` file that is part of the
release. Be aware that if you are working with environment variables in the
docker containers, the names might be different, because the variables are
interpreted from within the docker containers and not from the host machine. For
example `KARMEN_REDIS_HOST` is accessible as ``REDIS_HOST`` within the
container.

#### Deployment specific options

These should always be setup so your instance works as expected.

| Variable name              | Default                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `KARMEN_SECRET_KEY`        | `None`                         | A unique key that is used for session encryption.                                                                                                                                                                                                                                                                                                                                                                                                           |
| `KARMEN_FRONTEND_BASE_URL` | `None`                         | Base URL of Karmen Hub frontend. This is used as a base URL in e-mails,that Karmen Hub is sending ocassionally.                                                                                                                                                                                                                                                                                                                                             |
| `KARMEN_CLOUD_MODE`        | `0`                            | If on, the network scan feature is disabled and printers can be connected only via [websocket-proxy](https://github.com/fragaria/websocket-proxy). If off, you can connect to printers via,`http` or `https`.                                                                                                                                                                                                                                               |
| `KARMEN_SOCKET_API_URL`    | `None`                         | Base URL such as `http://path.to/websocket/api/%s` where the, [websocket-proxy](https://github.com/fragaria/websocket-proxy) is accepting connections. Used only when,`KARMEN_CLOUD_MODE` is enabled. The `%s` is replaced by device token during runtime.                                                                                                                                                                                                  |
| `KARMEN_MAILER`            | `dummy`                        | Type of mailer that is used in the backend to send e-mail. Supported values are,`ses`, `smtp`, `mailgun` and `dummy`. `Dummy` mailer only writes to a logfile, others are calling an external mail sending service. Mailers can be further configured with `KARMEN_MAILER_CONFIG`.                                                                                                                                                                          |
| `KARMEN_MAILER_FROM`       | `Karmen <karmen@karmen.local>` | Default sender of emails.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `KARMEN_MAILER_CONFIG`     | `{}`                           | JSON with configuration required by the selected `KARMEN_MAILER`. The JSON should be enclosed in `'` or escaped so the shell does not interpret its value. For `mailgun`: `{\"mailgun_domain\": \"...\", \"mailgun_api_key\": \"...\"}`. For `ses`: `{\"aws_secret_key\": \"...\", \"aws_access_key\": \"...\", \"aws_region\": \"...\"}`, for `smtp`: `{\"host\": \"...\", \"port\": \"...\", \"ssl\": \"...\", \"login\": \"...\", \"password\": \"...\"}` |

#### Advanced options

These can help you if your deployment requires some special care.

| Variable name                | Default          | Description                                                                                                                                            |
|------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `KARMEN_BACKEND_SENTRY_DSN`  | `None`           | [Sentry](https://sentry.io/) DSN to which the backend will log errors. If empty, no logging is being done.                                             |
| `KARMEN_FRONTEND_SENTRY_DSN` | `None`           | [Sentry](https://sentry.io/) DSN to which the frontend will log errors. If empty, no logging is being done.                                            |
| `KARMEN_HOST`                | `0.0.0.0`        | Host interface on which Karmen listens. This is useful when you need to restrict access.                                                               |
| `KARMEN_PORT`                | `80`             | Port on which Karmen listens for connections. This is useful if you are running Karmen in an environment shared with other services.                   |
| `KARMEN_UPLOAD_FOLDER`       | `./karmen-files` | Location of uploaded files. This directory is mounted as a volume into the container.                                                                  |
| `KARMEN_DB_DIR`              | `./db/data`      | Location of PostgreSQL data directory.                                                                                                                 |
| `KARMEN_BACKEND_HOST`        | `127.0.0.1`      | Host on which the backend API server listens.                                                                                                          |
| `KARMEN_BACKEND_PORT`        | `9764`           | Port on which the backend API server listens.                                                                                                          |
| `KARMEN_FRONTEND_HOST`       | `127.0.0.1`      | Host on which the frontend server listens.                                                                                                             |
| `KARMEN_FRONTEND_PORT`       | `9765`           | Port on which the frontend server listens.                                                                                                             |
| `KARMEN_POSTGRES_HOST`       | `127.0.0.1`      | Host of the PostgreSQL database. You don't have to use the dockerized instance bundled within the release.                                             |
| `KARMEN_POSTGRES_PORT`       | `5433`           | Port of the PostgreSQL database. You don't have to use the dockerized instance bundled within the release.                                             |
| `KARMEN_POSTGRES_DB`         | `print3d`        | Name of the PostgreSQL database. This DB is created for you during the first run.                                                                      |
| `KARMEN_POSTGRES_USER`       | `print3d`        | Username for the PostgreSQL database. This user is created for you during the first run.                                                               |
| `KARMEN_POSTGRES_PASSWORD`   | `print3d`        | Password for the PostgreSQL database. This password is set for the user during the first run.                                                          |
| `KARMEN_REDIS_HOST`          | `127.0.0.1`      | Host of Redis storage. You don't have to use the dockerized instance bundled within the release. However, protected instances are yet to be supported. |
| `KARMEN_REDIS_PORT`          | `6379`           | Port of Redis storage. You don't have to use the dockerized instance bundled within the release.                                                       |
| `KARMEN_NETWORK_TIMEOUT`     | `5`              | Timeout for HTTP reads in seconds.                                                                                                                     |
| `KARMEN_VERIFY_CERTIFICATES` | `1`              | Whether the app should verify HTTPS certificates. You should only change this setting if you know exactly what you are doing.                          |
