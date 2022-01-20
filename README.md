# MySQL Queries with Sakila Test Databass:


## 1. DB ER diagram:

![Sakila ER](./sakila_erd.png)




## 2. Setting Up Schema and Populate Database:

- **i. Setting UP schemas and Database:**

> ``tar -xf sakila-db.tar.gz -C <path>``

- **ii. Connect to the MySQL server:**

> ``mysql -u <username> -p``

- **iii. Create schema for sakila db**

``mysql> SOURCE <path>/sakila-db/sakila-schema.sql;``

- **iii. Populate database**

``mysql> SOURCE <path>/sakila-db/sakila-data.sql;``



## 3. Practice Questions:

**Basics:**

- Which actors have the first name ‘Scarlett’

- Which actors have the last name ‘Johansson’

- How many distinct actors last names are there?

- Which last names are not repeated?

- Which last names appear more than once?

- Which actor has appeared in the most films?

- Is ‘Academy Dinosaur’ available for rent from Store 1?

- Insert a record to represent Mary Smith renting ‘Academy Dinosaur’ from Mike Hillyer at Store 1 today .

- When is ‘Academy Dinosaur’ due?

- What is that average running time of all the films in the sakila DB?

- What is the average running time of films by category?

**Stored Procedure:**
- Create a basic stored procedure to display the first_name of the actor, provided actor_id.

## 4. Command Reference

- **1. Install the MySQL Server and complete the secure installation process as:**

> sudo apt-get install mysql-server

> sudo mysql_secure_installation

- **2. Modify the root authentication mechanism by first entering into the MySQL shell as:**

    - ``sudo mysql``

    - ``ALTER USER 'root'@'localhost'   IDENTIFIED WITH mysql_native_password BY
    '<password>';
    FLUSH PRIVILEGES;
    exit``

    - To test the work ``mysql -u root -p``

- **3. Backup Database Dump:**

> mysqldump -u root -p [db_name] > db_dump.sql


**4. Restore from Dump:**

> mysqldump -u root -p [db_name] < db_dump.sql

**5. Password policy:**

```sql
SHOW VARIABLES LIKE 'validate_password%';
```

```sql
+--------------------------------------+-------+
| Variable_name                        | Value |
+--------------------------------------+-------+
| validate_password.check_user_name    | ON    |
| validate_password.dictionary_file    |       |
| validate_password.length             | 6     |
| validate_password.mixed_case_count   | 1     |
| validate_password.number_count       | 1     |
| validate_password.policy             | LOW   |
| validate_password.special_char_count | 1     |
+--------------------------------------+-------+
```

**6. Modify Policy:**

```sql
SET GLOBAL validate_password.length = 6;
SET GLOBAL validate_password.number_count = 0;
```

**7. Create user and Assign Database:**

```sql
mysql> CREATE USER '<User>'@'<Host>' IDENTIFIED BY '<password>';

-- caution !! User can have same access as root
-- % -> refers to valid hosts existing in system
mysql> GRANT ALL PRIVILEGES ON *.* TO '<USER>'@'%';


-- provide access to specific database;
mysql> GRANT ALL PRIVILEGES ON <DB>.* TO '<USER>'@'%';

--update privilates
mysql> FLUSH PRIVILEGES;
```