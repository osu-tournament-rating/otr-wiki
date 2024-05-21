# Database Maintenance

## Setup

o!TR relies on a PostgreSQL database instance to function. This page can be used as a reference for first-time database setup as well as for disaster recovery.

It is recommended to run your dev database inside of a docker image.

First, create a docker volume:

```sh
docker volume create otr-db
```

Then start the database:

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

Backup the database:

```sh
docker exec [container] pg_dump -c -U postgres postgres | gzip > /my/dir/dump.gz
```

Restore the database:

> NOTE: If you already have a populated database and are encountering errors, run the following. This is strongly recommended regardless of whether you get errors to ensure a clean import.
> 
> 1. Remove the `public` schema:
>
> ```sh
> docker exec -it [container] psql -U postgres -c "DROP SCHEMA public CASCADE;" postgres 
> ```
>
> 2. Create the `public schema`:
>
> ```sh
> docker exec -it [container] psql -U postgres -c "CREATE SCHEMA public;" postgres 
> ```

Overwrite your database with the dump:

```sh
gunzip -c /my/dir/dump.gz | docker exec -i [container] psql -U postgres postgres 
```