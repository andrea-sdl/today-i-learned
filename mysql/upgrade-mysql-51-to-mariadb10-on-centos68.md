# Upgrading mysql from 5.1 to mariadb 10 on centos 6.8 #
quick and dirty reminder on how to upgrade

ref: https://mariadb.com/resources/blog/upgrading-mysql-51-mariadb-100-centos-6

## creating repo files
creating both the repo files 
* mariadb55.disabled for the maria 5.5 repo
* mariadb10.disabled for the 10 repo.

## dumping and backup

```sh
mysqldump --all-databases --user=root --password > full_backup.sql
cp /etc/my.cnf /etc/my.cnf.bak
service nginx stop
service mysqld stop
cp -R /var/lib/mysql /tmp/mysql51_backup
```
## Migrating to 5.5
```sh
cd /etc/yum.repos.d
mv mariadb55.disabled mariadb55.repo
yum clean all
yum remove mysql-server
yum install mysql-server
service mysqld start
mysql_upgrade -p
```

### Check the db
Now that the 5.5 migration is done, check the db by connecting 

## Migration to mariadb 10

```sh
service mysql stop
yum remove mysql-server mysql-client
mv mariadb55.repo mariadb55.disabled
mv mariadb10.disabled mariadb10.repo
yum clean all
yum install mysql-server mysql-client
service mysqld start
mysql_upgrade -p
```

### Check the db
Now that the 10 migration is done, check the db by connecting 

### Check and adapt config files
```sh
cat /etc/my.cnf
```

## cleaning it up 
check the my.cnf.back and the mysql51_backup and in case delete it.