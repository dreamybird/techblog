# A bash script to backup Mysql databases

I often faced similar situations when I should just make backups of my databases. I can just save to file system. Every time I write new script. Now I decided to write similar script last time.  I hope the script will help you too.

```bash
#!/bin/bash

# Version 20151021
# The script serves to backup each database to separate file in the a directory


DATABASE_BACKUP_LIST=$(mysql -e 'show databases' -sN 2>/dev/null|egrep -v 'information_schema|performance_schema|mysql')
FILENAME_DATE_TEMPLATE=$(date +%Y-%m-%d-%H-%M-%S)
SUBFOLDER_DATE_TEMPLATE=$(date +%Y-%m-%d)
MYSQLDUMP='/usr/bin/mysqldump'

printUsage(){
   echo  "Usage: "$(basename $0)" backupdir"
   exit 1
}

printError(){
   echo "Error: $1"
   exit 1
}

[ $# -ne  1 ] && printUsage
BACKUP_DIR=$1

cd $BACKUP_DIR || printError "Cannot change current directory to $BACKUP_DIR. May be the path is wrong."
[ -w $BACKUP_DIR ] || printError "Cannot write to $BACKUP_DIR. Check permissions of the directory."

[ -x $SUBFOLDER_DATE_TEMPLATE ] || mkdir $SUBFOLDER_DATE_TEMPLATE || printError "Cannot create $SUBFOLDER_DATE_TEMPLATE in $BACKUP_DIR"

for DB in $DATABASE_BACKUP_LIST; do
   echo "Backuping $DB..."
   $MYSQLDUMP $DB|gzip > $BACKUP_DIR/$SUBFOLDER_DATE_TEMPLATE/$DB-$FILENAME_DATE_TEMPLATE.sql.gz
done
cd ->/dev/null

```
