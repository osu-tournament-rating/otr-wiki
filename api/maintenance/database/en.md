# Database Maintenance

## Backup & Restore

o!TR relies on a PostgreSQL database instance to function. Production backups are automated via a script set to run every six hours. The backups are compressed and uploaded to a Google Cloud storage bucket. At this time, only Stage can perform and manage these operations, though the procedures are documented publicly as we plan to support distribution of small test databases for those wanting to develop locally.

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