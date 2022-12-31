# homeserver
**NB: This is not intended to be useful (except perhaps as a reference) for anyone other than myself.**

My simple homeserver setup, running the following using Docker Compose:
- [AdGuard Home](https://adguard.com/en/adguard-home/overview.html)
- [Nextcloud](https://nextcloud.com/)
- [calibre-flask](https://github.com/carderne/calibre-flask) (I don't use the popular [calibre-web](https://github.com/janeczku/calibre-web) because it doesn't have a simple HTML interface for  Kindles)
- [lifx-night-light](https://github.com/carderne/lifx-night-light)

Mostly copied from [runtipi](https://github.com/meienberger/runtipi) and [runtipi-appstore](https://github.com/meienberger/runtipi-appstore), without the traefix reverse proxy, or the management API.

## File structure
Each service has a directory (`books`, `lifx` etc), with (up to) two folders in each:
- `conf`: optionally version-controlled
- `data`: user or app data

## Install Docker and Compose
Steps 1 and 2 from [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04) and then:
```bash
apt install docker-compose-plugin
```

## Modifications
In [.env](.env), set the `APP_DOMAIN`, and `_USERNAME` and `_PASSWORD` variables to more useful values, if necessary. The latter will default to `admin/admin` if not set.

## ARM versions of images
You may need to locally build the images for [calibre-flask](https://github.com/carderne/calibre-flask) and [lifx-night-light](https://github.com/carderne/lifx-night-light), if the DockerHub versions don't support your CPU arch.

## Run
```bash
docker compose up --detach
```

## Port 53 issue with AdGuard
[Solution here](https://github.com/AdguardTeam/AdGuardHome/wiki/Docker#resolved-daemon)
