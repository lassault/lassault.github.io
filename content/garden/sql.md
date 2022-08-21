---
title: "SQL 💾"
date: 2019-01-01
lastmod: 2021-12-15
draft: false
garden_tags: ["sql"]
summary: "Code snippets with useful stuff about SQL"
status: "growing"
---

Code snippets with useful stuff about SQL

## Users

#### Create a user in MySQL [^1]
```mysql
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON <database> . <tables> TO 'user'@'localhost';
FLUSH PRIVILEGES
```

[^1]: <a href="https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql" target="_blank">How to create a new user and grant permissions in MySQL</a>

#### Remove a user and it's privileges in MySQL [^2]
```mysql
SHOW GRANTS FOR 'user'@'localhost'; -- To see the user privileges
REVOKE ALL PRIVILEGES ON <database> . <tables> TO 'user'@'localhost';
DROP USER 'user'@'localhost';
```

[^2]: <a href="https://stackoverflow.com/questions/17799806/remove-privileges-from-mysql-database" target="_blank">Remove privileges from MySQL database</a>

## Import/export databases
```bash
# Import database
mysql -u <user> -p <database> < database.sql

# Export database
mysql -u <user> -p <database> > database.sql
```

## Alter tables [^3]
```mysql
-- Add the AUTO_INCREMENT option
ALTER TABLE <table> MODIFY <value> INT NOT NULL AUTO_INCREMENT;
```

[^3]: <a href="https://mariadb.com/kb/en/auto_increment/" target="_blank">Add AUTO_INCREMENT option</a>

## Times
If you want to add or substract two times, simply use ADDTIME and SUBTIME.

```mysql
SELECT ADDTIME('14:00:00', '00:15:00');                

+---------------------------------+
| ADDTIME('14:00:00', '00:15:00') |
+---------------------------------+
| 14:15:00                        |
+---------------------------------+
1 row in set (0.00 sec)

SELECT SUBTIME ('14:00:00', '00:15:00');

+----------------------------------+
| SUBTIME ('14:00:00', '00:15:00') |
+----------------------------------+
| 13:45:00                         |
+----------------------------------+
1 row in set (0.00 sec)
```

It also works with dates, and you can substract hours, minutes, seconds and fractional seconds.