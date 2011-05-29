When I tried to insert about 300K records into the postgres database using activerecord-import I was getting this error.

`stack level too deep
/Users/ajay/Developer/.rvm/gems/ruby-1.9.2-p180@movies/gems/activerecord-import-0.2.7/lib/activerecord-import/adapters/abstract_adapter.rb:54`

Instead of saving all the records at one shot I have split my entries into multiple arrays

    cast_and_crew.each_slice(100) do |slice|
      CastAndCrew.import ["celebrity_role_id", "movie_id", "celebrity_id"], slice, :validate => false
    end
