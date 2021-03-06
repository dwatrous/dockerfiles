# Hastebin

[Hastebin](https://github.com/seejohnrun/haste-server) is a simple
pastebin, which can be installed on a protected network.

This dockerfile builds an image that can be configured using
environment variables. This is done by writing `config.js` at runtime
from interpolated variables in `app.sh`.

See `app.sh` for variable names.

## Example use

Writing pastes to a mounted local volume:

```
docker run --name hastebin -d -p 7777:7777 -e STORAGE_TYPE=file -e /data:/app/data rlister/hastebin
```

Writing pastes to redis:

```
docker run --name redis -d redis
docker run --name hastebin -d -p 7777:7777 --link redis:redis -e STORAGE_HOST=redis rlister/hastebin
```
