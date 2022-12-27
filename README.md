# homeserver
Mostly copied from:
- https://github.com/meienberger/runtipi
- https://github.com/meienberger/runtipi-appstore

```bash
docker compose up
```

## File structure
Each service has a directory (`books`, `lifx` etc), with (up to) two folders in each:
- `conf`: optionally version-controlled
- `data`: user or app data
