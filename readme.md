Download the container file

```
curl -LOk https://github.com/bcsjk11/COMP5210-mini-press/archive/master.zip && \
unzip master.zip && \
rm -rf master.zip
```

Go into the folder

```
cd COMP5210-mini-press
```

Run the container

```
docker-compose up -d
```

Run the wordpress setup

```

http://localhost/

```

If the database does not exist do this:

```
docker exec -it wp_mysql_5210 bash

mysql -u root -p -e "create database db5210"; 

```

Create back up of your database

```
mysqldump --add-drop-table -h wp_mysql_5210 -u root -p db5210 > /var/lib/mysql/backup.sql
```

Copy the backup.sql file into your main wp folder

```
cp databases/wp_mysql_5210/backup.sql .
```

Commit to git

Create a .gitignore file with the following:

* databases/