Normal ActiveRecord callbacks will NOT be called when using activerecord-imports. This is because it is mass importing rows of data and doesn't necessarily have access to in-memory ActiveRecord objects. 

If you do have a collection of in-memory ActiveRecord objects you can do something like this:

```
books.each do |book|
  book.run_callbacks(:create)
end
Book.import(books)
```