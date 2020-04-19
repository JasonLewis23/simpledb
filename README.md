SimpleDB
Author: Jason Lewis <jclewis2323@gmail.com>

Description:

SimpleDB is a bash utility for storage and retrival of data, inlcluding log style storage and dictionary style storage.
Users may add data through the command line or stdin. Databases can be copied, archived, and un-archived. Written in bash
and only intended for use in linux environments that include common linux utilities, such as grep, awk, sed, cat, etc.

	Supported database types
		- dict - dictionary
		store data in key=value pairs
		- log - log file
			store data as a typical log file

	Supported get (-g) types
		- dict
			- key
				get entries that match the passed in key
			- rkey
				get entries that contain the passed in key

	Supported remove (-r) types
		- dict
			- key
				remove entries that match the passed in key
			- rkey
				remove entries that contain the passed in key

Install:

Run the following command (may require sudo permissions)
	- cp simpledb /usr/bin

Usage:

	-h - display help screen"
	-q - suppress output"
	-c <type> <dname> - create a new database, dname, with one of the following types, type:"
	-s <dname> - set the database dname to the current database"
	-us - unset the current database"
	-d - delete current database"
	-p - print raw text of current database"
	-a - add entry to current database from stdin"
	-as - add entry to current database from passed in string"
	-cp <dir> - copy database file to directory"
	-ar - archive current database"
	-uar <dname> - unarchive database dname"
	-la - list archived databases"
	-g <type> <str> - get an entry from the current database (if the database supports the type of get)"
	-r <type> <str> - delete an entry from the current database (if the database supports the type of delete)"
	-gc - get current database name and type"
	-pt - print delimeter torken for dict type"

Examples:

	Create a database
		simpledb -c dict mydb.dict

	Changing current database
		simpledb -s mydb.dict
		simpledb -us
		simpledb -d

	List databases
		simpledb -l
		simpledb -la

	Printing
		simpledb -p
		simpledb -gc
		simpledb -pt

	Add to a database
		simpledb -a < input.txt
		simpledb -am "hello<<DTOK>>world!"

	Remove from a database
		simpledb -r key hello

	Get from a database
		simpledb -g key hello

	Archiving
		simpledb -ar
		simpledb -uar mydb.dict
