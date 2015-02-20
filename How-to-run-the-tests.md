CI test results are here: https://travis-ci.org/zdennis/activerecord-import/

## Configure Databases ##
* copy ``test/database.yml.sample`` to ``test/database.yml``
* modify ``test/database.yml`` for your database settings
* create databases as needed

## Run Tests ##

The tests run against different databases and active record versions.  This is one example of how to run the tests

    rm Gemfile.lock
    AR_VERSION=4.2 bundle install
    AR_VERSION=4.2 bundle exec rake test:postgresql test:sqlite3 test:mysql

