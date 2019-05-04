# 100 Days of Code Log

### Day 1: May 1st, 2019
#### Today's Progress
Finished the [Pokemon Scraper Lab Bonus tests](https://github.com/big32mike/pokemon-scraper-online-web-pt-021119)
- Named and optional arguments and metaprogramming facilitate saving objects to a persistent data store
- SQLite gem DB queries return an array of rows, of which the rows are arrays of columns

Completed the 2 ORM mapping labs.
- We setup DB[:conn] constant hash in environment.rb and use it to talk to the database.
- The example ORM initializes the object's id to nil so we can write it after the db has generated it with its autoincrement feature. We set the instance varible directly inside a save method, since it's an attr_reader.
- Tables represent Classes and rows instance objects

[ORM mapping to table lab](https://github.com/big32mike/orm-mapping-to-table-lab-online-web-pt-021119/blob/master/lib/student.rb)  
[ORM mapping db to Ruby object lab](https://github.com/big32mike?tab=repositories)

### Day 2: May 2nd, 2019
Completed the Updating Records in an ORM lab.
- Implemented the find or create pattern with the db
- instantiate object, save to db, set db-generated key field in object
- save all attributes to db when updating

Completed Bringing it all Together lab.
- prevent duplication via find or create methods
- reinforced the pattern of mapping an object to a db row, then writing the unique identifier generated by the db
- that unique identifier should be an attr_reader vs accessor, because we don't want it changed once the db writes it
- we set it using instance variable in a .save method

### Day 3: May 3rd, 2019
Completed Dynamic ORMs lab
- The pattern of first creating the database table and having your program do all the work of writing your ORM methods based on that table is exactly how we'll develop web apps in Sinatra and Rails
- It seems like a best practices to put the IF (NOT) EXISTS constraints on creating and dropping db tables.
- introduces the #results_as_hash method of the SQLite3 gem that returns database rows as a hash using the column names as keys, instead of an array of array rows
- `PRAGMA table_info("#{table_name}")` sql keyword to get the column names of a table.
 - the table_name class method doesn't require self when in the Class context(ie another class method)
- Array#compact removes nil values
- Using self.class to refer to class methods inside instance methods
- ORM insert methods ignore nil columns, since the id hasn't been generated yet
- ORM update methods ignore the id column. since it's an attr_accessor due to metaprogramming, we account for it here so we don't overwrite the original value.
