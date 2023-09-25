## deploy
```shell
docker compose up -d pg api admin
docker compose exec -it pg createdb -U postgres FKS
docker compose exec -it admin ./.venv/bin/python main.py db -u
docker compose exec -it admin ./.venv/bin/python main.py createsuperuser -u {username} -p {password}
docker compose exec -it admin ./.venv/bin/python main.py fill --students
docker compose up -d nginx
```

## dump & restore
```shell
docker compose exec -it pg pg_dump -U postgres FKS > "$(date +"~/project/backups/%Y_%m_%d_%H_%M_%S").sql"
docker compose exec -T pg psql -U postgres FKS < {filename}
```