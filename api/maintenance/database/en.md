# Database Maintenance

## Setup

o!TR relies on a PostgreSQL database instance to function. This page can be used as a reference for first-time database setup as well as for disaster recovery.

It is recommended to run your dev database inside of a docker image.

First, create a docker volume:

```sh
docker volume create otr-db
```

```sh
docker run -d -p 5432:5432 -v otr-db:/var/lib/postgresql/data -e POSTGRES_PASSWORD=password postgres
```

In the above example, this is what you put as your `DefaultConnection` in the `otr-api` `appsettings.Development.json` file:

```
Server=localhost;Port=5432;User Id=postgres;Password=password;Include Error Detail=true;
```

Now comes the question of populating your database. If you are on the dev team, reach out to [Stage](https://osu.ppy.sh/users/8191845) for a dump. Otherwise, please wait for a public dump to be made available.

If you have a database dump, you can populate your database by following the restore instructions below.

## Backup & Restore

Production backups are automated via a script set to run every six hours (soon, a hash check will be performed so identical backups won't be created, thus saving resources). The backups are compressed and uploaded to a Google Cloud storage bucket. At this time, only [Stage](https://osu.ppy.sh/users/8191845) can perform and manage these operations, though the procedures are documented publicly as we plan to support distribution of databases for those wanting to develop locally / verify our dataset.

Backups are done with `pg_dump` and restores are done with `psql` as documented [here](https://www.postgresql.org/docs/current/backup-dump.html#BACKUP-DUMP).

The following will backup the database as specified in our `docker-compose` files:

```sh
docker exec db pg_dump -c -U postgres postgres | gzip > /my/dir/dump.gz
```

To restore:

```sh
gunzip -c /my/dir/dump.gz | docker exec -i db psql -U postgres postgres 
```

If the database instance is not running in docker, ignore the `docker exec` command.