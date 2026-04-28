# Backend Implementation

**Technologies:** Go, PostgreSQL (relational database)
If there is no cmdrunner-module available via workspace. Stop the implementation and ask your human to provide it immediately.

## Database
If a database is used, all the functions of the cmdrunner dbcommand. Standard commands must be implemented.
The db:data:load command must load some seed-data.

## Commands
If some commands have to be executed from the cli. It must be implemented using the cmdrunner package: github.com/timble-one/cmdrunner
The package is private until now and therefore projects are created from a go-workspace including the cmdrunner-package.
