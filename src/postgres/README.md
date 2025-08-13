# Postgres - Practice Assignment

This file describes how to manipulate the
Postgres server so that you can work through the
Postgres chapters in our text.

## Starting and connecting to the Postgres server

1. Open your personal repository via the link you have been provided.

2. In the terminal, navigate to the postgres directory:

    ```bash
    cd src
    cd postgres
    ```

3. Start the Postgres server (this may take a minute or two the first time)

    ```bash
    ./up.bash
    ```

4. Connect to the Postgres server

    ```bash
    ./shell.bash
    ```

Your prompt should be `7dbs=# `.

5. Create a table called 'trees' using the code below. You must use the exact upper or lower case and the exact punctuation.
```
CREATE TABLE trees (
  tree_name varchar(30) PRIMARY KEY, 
  height_range varchar(20)
);
```

6. Check to see if you have correctly created the table:
```
SELECT * FROM trees;
```
You should see somthing like: 
```
 tree_name | height_range 
-----------+--------------
(0 rows)
```

7. Add two trees to the database:
```
INSERT INTO trees (tree_name, height_range)
VALUES ('Red Maple','40-60 ft'), ('Douglas Fir', '70-300 ft');
```

9. Check to ensure that the two trees have been added:
```
SELECT * FROM trees;
```
10. Add two two trees of your choice to the database.
11. Display the ```tree``` to ensure that you have correctly added your two trees. 
    
12. When you are done interacting with the Postgres server, type `exit` or `\q`
to return to the bash prompt. This does not stop the server, it just
disconnects you from the server. You can reconnect by running `./shell.bash`
again.

## Saving the database state

13. Save your databased. Assuming your Postgres server is running, and your terminal is still
positioned in the `postgres/` directory, run the following...

```bash
./save.bash trees.sql
```

This dumps the database into a file named `trees.sql`.

## Stopping and delete the Postgres server
14. Stop the Postgres server
```bash
./down.bash
```

15. Commit your changes by clicking the blue "Commit" button in the upper left portion
of your screen.

## Loading the database state

After starting a new Postgres server, it will be
empty. Assuming you saved the state of your database
in `trees.sql`, you can restore the currently empty
server to this state as follows.

```bash
./load.bash trees.sql
```

## Best Practice

Postgres is saving your data inside a Docker container (a virtual machine)
inside a GitHub codespace (a virtual machine).

Do not run `./down.bash` before saving your data as it
destroys the container running your DBMS.

So to protect your data, I recommend that when you are done working,
save your database to an SQL file, take down your DBMS, and then
save and stop your workspace as follows:

    ./save.bash mydb.sql
    ./down.bash
    save-and-stop

When you sit down to work again, go to your repo on GitHub, reposition
into `postgres/`, bring up your DBMS, and load it with your SQL file as
follows:

    cd postgres
    ./up.bash
    ./load.bash mydb.sql

Now you are ready to continue your work.

16. Try this now to ensure that it works. 
