<!-- prepared statement -->

-   [data integrity](#data-integrity)
-   [string](#string)
-   [strict mode](#strict-mode)
-   [query performance](#query-performance)

### data integrity

-   Unique constraint can be made of multiple columns.
-   DB adds `CONSTRAINT` keyword if not added. Constraints can have name which is helpful for debugging.

```sql
CREATE TABLE customers(
  email varchar(50) NOT NULL,
  user_name varchar(50) NOT NULL,
  phone varchar(50) NOT NULL,
  CONSTRAINT unique_phone_number UNIQUE(phone),
  UNIQUE(user_name, email)
);
```

### string

-   `QUOTE()`: can be used to quote string.

-   Multiple string side by side without any delimiter will be concatenated to a single string.

```sql
SELECT 'Hello' 'World'; -- HelloWorld
```

### strict mode

-   When strict mode is disabled, warnings will be shown and query will be executed.
-   When strict mode is enabled, error will be thrown and query won't be executed.

-   PostgreSQL does not have a "strict mode" like MySQL. However, PostgreSQL is generally more strict than MySQL by default. For example, PostgreSQL does not perform automatic type conversion as liberally as MySQL does in non-strict mode, and it does not truncate or adjust data to fit into a column like MySQL does in non-strict mode.

mysql has two modes:

-   global
-   session

session is made when a user is logged in and the connection is persistent. By default, global `sql_mode` is used in every session.

`STRICT_ALL_TABLES` should be preferred instead of `STRICT_TRANSz_TABLES`

```sql
SELECT @@GLOBAL.sql_mode;
SELECT @@SESSION.sql_mode;
SHOW VARIABLES LIKE '%sql_mode%';

-- config for session
SET sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_ALL_TABLES'; -- some rules are applied
SET sql_mode = @@GLOBAL.sql_mode; -- global settings are applied
SET sql_mode = ''; -- nothing is applied
```

### query performance

-   subquery executes for each row while join executes once per
