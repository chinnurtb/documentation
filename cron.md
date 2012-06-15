# Doing a database backup each 10 Minutes

```
# m h  dom mon dow   command
 */10 *    * * *   cd ~/mysql-git-backup && ./dump-mysql.sh && ./backup-git.sh
```

# listing all cronjobs

```
cronjob -l
```
