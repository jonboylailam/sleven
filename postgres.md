Command      | Description
------------ | -------------
psql -U postgres | login
\c dbname | Connect to db
alter database dbName rename to dbName | Rename a database
\l | List databases
\dn | List schemas
\dt | List tables
\d tableName | List columns
pg_dump dbName dump.sql | Dump a database to file
drop schema schemaName cascade | Drop a schema in a database
