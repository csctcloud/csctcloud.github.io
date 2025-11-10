# Login to MySQL on CSCT Cloud
You need to login to a database user account to access the MySQL server installed on CSCT Cloud. You can derive the username and password for your user account using the rules below.

Your account will have access to two databases/schemas, where you can create tables and records for your projects, as well as for practical exercises.

These databases are named after your account username:

* `<your username>`
* `<your username>_prj`

## Your database account username
Your username can be derived from your UWE email address:

1. Remove the domain portion of your email address (`@live.uwe.ac.uk`)
2. Remove all special characters (`.` and `-`)
3. The resulting text is your username

!!! example
    Anton has a UWE email address of `anton.jack-hammer@live.uwe.ac.uk`, so his database account username would be `antonjackhammer`.

## Your initial password
When your database is first created an initial password is generated, based off your username. You can work out your password once you have derived your username:

1. Capitalise the first and last letters of your username
2. Append the total number of characters in your username
3. Append the string `+$++`
4. The resulting string is your password

**Once you have your initial password and have logged in to the database server, you should change your password using the steps below.**

!!! example
    Anton would build his password like so:

    | Username        | Capitalise first and last | Append length     | Append special characters |
    | --------------- | ------------------------- | ----------------- | ------------------------- |
    | antonjackhammer | AntonjackhammeR           | AntonjackhammeR15 | AntonjackhammeR15+$++     |

    So, Anton's initial password to login to the database server would be: `AntonjackhammeR15+$++`.

## Changing your password
It is import you change your database account password from the one we initially generate for you, otherwise other users are able to derive your password and login to the database server as you.

Once you have connected to the database server [using the CLI](./cli.md), run the command below to change your password:

``` sql
ALTER USER <username> IDENTIFIED BY ‘<new password>’;
```

!!! example
    If Anton wanted to change his password to `SecretNewPassword67!!`, he would run the command:

    ``` { .sql .no-copy }
    ALTER USER antonjackhammer IDENTIFIED BY 'SecretNewPassword67!!';
    ```

Your new password should have:

* At least 8 characters
* A mix of uppercase and lowercase characters
* At least one number
* At least one special character