# homeserver
**NB: This is not intended to be useful (except perhaps as a reference) for anyone other than myself.**

My simple homeserver setup, running the following using Docker Compose:
- [AdGuard Home](https://adguard.com/en/adguard-home/overview.html)
- [calibre-flask](https://github.com/carderne/calibre-flask)
- [calibre-web](https://github.com/janeczku/calibre-web) (much better, but doesn't have a simple HTML interface for  Kindles)

Mostly copied from [runtipi](https://github.com/meienberger/runtipi) and [runtipi-appstore](https://github.com/meienberger/runtipi-appstore), without the traefix reverse proxy, or the management API.

## File structure
Each service has a directory (`books` etc), with (up to) two folders in each:
- `conf`: optionally version-controlled
- `data`: user or app data

## Install Docker and Compose
Steps 1 and 2 from [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04) and then:
```bash
apt install docker-compose-plugin
```

## Secrets
```bash
cp .env.example .env
```

And then modify the `USERNAME`/`PASSWORD` variables in that file.
They will default to admin/admin if not set.

## App-specific setup
### books
Symlink the folder containing the books:
```bash
ln -s /path/to/your/calibre/dir books/data
```

### fava
```bash
mkdir -p fava/data
ln -s /path/to/beancount/dir fava/data/accounts
```

### Adguard network setup
https://www.smarthomebeginner.com/adguard-home-docker-compose-guide/

## Run
```bash
docker compose up --detach
```
