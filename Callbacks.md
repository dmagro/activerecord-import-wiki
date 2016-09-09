Normal ActiveRecord callbacks will NOT be called when using activerecord-imports. This is because it is mass importing rows of data and doesn't necessarily have access to in-memory ActiveRecord objects. 

If you do have a collection of in-memory ActiveRecord objects you can do something like this:

```
books.each do |book|
  book.run_callbacks(:save) { false }
  book.run_callbacks(:create) { false }
end
Book.import(books)
```

This will run before_create and before_save callbacks on each item. The `false` argument is needed to prevent after_save being run, which wouldn't make sense prior to bulk import.