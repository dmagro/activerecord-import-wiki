[MySQL](http://dev.mysql.com/doc/refman/5.0/en/insert-on-duplicate.html), [SQLite](https://www.sqlite.org/lang_insert.html), and [PostgreSQL](https://www.postgresql.org/docs/current/static/sql-insert.html#SQL-ON-CONFLICT) (9.5+) support `on_duplicate_key_ignore` which allows you to skip records if a primary or unique key constraint is violated.

## Example

```ruby
book = Book.create! title: "Book1", author: "FooManChu"
book.title = "Updated Book Title"
book.author = "Bob Barker"

Book.import [book], on_duplicate_key_ignore: true

book.reload.title  # => "Book1"     (stayed the same)
book.reload.author # => "FooManChu" (stayed the same)
```

### Conflict with ActiveRecord uniqueness validation

Don't use ActiveRecord uniqueness validator - it will make the update not happen.
Use unique index on the database column if needed.