# backup-database

MariaDB/MySQL database backup script for performing full backups.

mysqldump can be a bit peculiar when dealing with triggers, forcing you to
dump different database components separately or risking not being able to
restore from the backup.

This script essentially does the following:

1. Extract structure (tables, views, procedures)
2. Extract data
3. Extract triggers
4. Compress

To be able to access the database the user executing the script must either have
login credentials in `~/.my.cnf` or place the credentials into the script. The
former alternative is prefable and should always be used if anyone else has
access to the script.

```
Usage: $(basename ${BASH_SOURCE[0]}) [options] <database>

    -o FILE   Output to FILE, default is '<database>-YYYYMMDD.sql.gz'
    -l        Log to syslog
    -s        Be silent
    -t DIR    Use DIR instead of '/tmp/' for temporary files
    -h        Show this help message and exit
    -v        Show version and exit
```
