# aozora-hack-api
青空文庫REST APIサーバー

## How to Run

- build docker image
```
docker build -t aozora_hack_api .
```

- wakeup your postgresql server
- create secret file with postgresql connection config

```
mkdir .secret
echo POSTGRES_HOST={YOUR_POSTGRESQL_HOST} > .secret/env
echo POSTGRES_PASSWORD={YOUR_PASSWORD} >> .secret/env
```

- initialize database

```
docker run --rm -it --env-file .secret/env aozora_hack_api bundle exec rails db:create
```

- wakeup server

```
docker run -d -p 3000:3000 --env-file .secret/env aozora_hack_api
```
