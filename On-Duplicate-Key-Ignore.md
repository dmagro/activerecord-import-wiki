[MySQL](http://dev.mysql.com/doc/refman/5.0/en/insert-on-duplicate.html), [SQLite](https://www.sqlite.org/lang_insert.html), and [PostgreSQL](https://www.postgresql.org/docs/current/static/sql-insert.html#SQL-ON-CONFLICT) (9.5+) support `on_duplicate_key_ignore` which allows you to skip records if a primary or unique key constraint is violated.

### Conflict with ActiveRecord uniqueness validation

Don't use ActiveRecord uniqueness validator - it will make the update not happen.
Use unique index on the database column if needed.