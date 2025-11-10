# Connect to MySQL using the shell
## Login to the database server
After connecting to CSCT Cloud using [the terminal](../connecting/terminal.md), enter the command below to login to MySQL using your database account username - you will be prompted to enter your password:

``` bash
mysql -u <username> -p
```

If you haven't already, you can derive your database account username and initial password using the steps [on the previous page](./login.md).

!!! danger
    It is import you change your database account password from the one we initially generate for you, otherwise other users are able to derive your credentials and login to the database server as you.

    If you haven't changed your password yet, [**do this now**](./login.md#changing-your-password).

## Interacting with the MySQL shell
Now you're connected to the MySQL shell, there are a number of different commands you have been granted permission to run. You'll learn about these and the semantics for performing different queries in your lab sessions.

For now, try running the commands below to practice using the MySQL shell.

!!! note
    SQL commands entered into the shell should be terminated with a semicolon (`;`).

### Select a database
You can change the database you're working on using the `USE` command, e.g. to select `STUDENTSREG`, the database of example student records:

``` { .console .no-copy }
mysql> USE STUDENTSREG;
Database changed
```

### View tables in database
List tables using the `SHOW` command:

``` { .console .no-copy }
mysql> SHOW TABLES;
+--------------------------+
| Tables_in_STUDENTSREG    |
+--------------------------+
| Agent Data               |
| Agent_Data               |
| Agent_Table              |
| BIGTABLE                 |
| BOYS                     |
| Bookings                 |
| CSSTUDENTS               |
| Cancellations            |
...
```

### View structure of a table
View a table's structure using the `DESCRIBE` command:

``` { .console .no-copy }
mysql> DESCRIBE STUDENT;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| SID      | varchar(10) | NO   | PRI | NULL    |       |
| SNAME    | varchar(30) | YES  |     | NULL    |       |
| EMAIL    | varchar(40) | YES  |     | NULL    |       |
| Tutor_Id | varchar(10) | YES  | MUL | NULL    |       |
| MID_ID   | varchar(45) | YES  | MUL | NULL    |       |
+----------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

### Select records from table
Select records using the `SELECT` command:

``` { .console .no-copy }
mysql> SELECT * FROM STUDENT;
+-------+--------------------------+-------------------------+----------+--------+
| SID   | SNAME                    | EMAIL                   | Tutor_Id | MID_ID |
+-------+--------------------------+-------------------------+----------+--------+
| 1000  | Abdul Basit Chaudhry     | abc@abc.com             | 1000     | NULL   |
| 1001  | Daniel Everret Fernandes | def@def.com             | 1004     | NULL   |
...
```

## Disconnecting from the server
When you're finished working on the database server, use the `QUIT` command to disconnect from the MySQL shell.

``` { .console .no-copy }
mysql> QUIT;
Bye
```