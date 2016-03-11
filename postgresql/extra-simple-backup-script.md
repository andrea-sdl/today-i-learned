# Extra simple backup script for PostgreSQL #

This script isn't very complex but it's a good start when you want to setup a dead-simple way to backup your postgresql every day and every month. 

```bash
DOW=$(date +%a)
MONTH=$(date +%m)
mkdir -p backups
pg_dumpall --database=DBNAME --username=USERRNAME | bzip2 > backups/backup_pg_${MONTH}_${DOW}.sql.bz2
```