## Setup your wordpress instance

**Download the container file**

```
curl -LOk https://github.com/bcsjk11/COMP5210-mini-press/archive/master.zip && \
unzip master.zip && \
rm -rf master.zip
```

**Go into the folder**

```
cd COMP5210-mini-press-master
```

**Run the container**

```
docker-compose up -d
```

**Run the wordpress setup**

```

http://localhost/

```

**If the database does not exist do this:**

```
docker exec -it wp_mysql_5210 bash

mysql -u root -p -e "create database db5210"; 

```

**Create back up of your database**

```
mysqldump --add-drop-table -h wp_mysql_5210 -u root -p db5210 > /var/lib/mysql/backup.sql
```

**Restore your back up of your database**

```
cp backup.sql databases/wp_mysql_5210/backup.sql
mysql -u root -p < /var/lib/mysql/backup.sql
```

**Copy the backup.sql file into your main wp folder**

```
cp databases/wp_mysql_5210/backup.sql .
```

**Commit to git**

Create a .gitignore file with the following:

* databases/

## Create a child Theme:

**Create a new folder in**  `COMP5210-mini-press-master/wp-content/themes/`

named, chosen theme with -child appended to it

**Open this folder in VSCode**

Create a style.css file

**Code Snippet for child Theme:**

```
/*
 Theme Name:   Twenty Fifteen Child
 Theme URI:    http://example.com/twenty-fifteen-child/
 Description:  Twenty Fifteen Child Theme
 Author:       John Doe
 Author URI:   http://example.com
 Template:     twentyfifteen
 Version:      1.0.0
 License:      GNU General Public License v2 or later
 License URI:  http://www.gnu.org/licenses/gpl-2.0.html
 Tags:         light, dark, two-columns, right-sidebar, responsive-layout, accessibility-ready
 Text Domain:  twenty-fifteen-child
*/
```