# job-workflow
Trick and tips for day-to-day work

## [I need PostgreSQL DB for my app](#postgres)

### postgres

Create docker volume for data or make dir.

```bash
docker volume create postgres-db-app1
```

```bash
mkdir /home/user/data/postgres-db-app1
```

Run docker with exposed default port 5432 and set pass for 'postgres' user.

Map postgres folder data to volume:

```bash
docker run -e POSTGRES_PASSWORD=pass_for_user_postgres -v /home/user/data/postgres-db-app1:/var/lib/postgresql/data -p 5432:5432 -d postgres:9.5
```

Map postgres folder data to folder:

```bash
docker run -e POSTGRES_PASSWORD=pass_for_user_postgres -v postgres-db-app1:/var/lib/postgresql/data -p 5432:5432 -d postgres:9.5
```

You can find next interesting:
- postgres:X.Y -> X.Y is [version/tag](https://hub.docker.com/_/postgres?tab=tags) you need (in above example is 9.5) 
- -e POSTGRES_USER=my_username -> use it in conjunction POSTGRES_PASSWORD with if you don't want to use default user 'postgres'
- --name [container_name] -> in case you want to give container name
