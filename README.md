# victims-reference-sync-client

Example of a clint which syncs victims-cve-db content into a local database for usage by a scanner.

# Install
Install the requirements:

* python3-GitPython.noarch
* python3-sqlalchemy
* python3-PyYAML

or use ``pip``:
```
$ pip install -r requirements.txt
```

# Usage

## Help
```
usage: victims-sync-client [-h] [-d] [-b BASE_PATH] [--db DB] {sync} ...

positional arguments:
  {sync}                sub-command help
    sync                Sync from the remote database

optional arguments:
  -h, --help            show this help message and exit
  -d, --debug
  -b BASE_PATH, --base-path BASE_PATH
  --db DB               Database URI to store data in
```

## Example
```
$ ./victims-sync-client -b /tmp/ sync
$ ls -la test.db 
-rw-r--r--. 1 steve steve 151552 Jan 25 10:19 test.db
$ ./victims-sync-client -b /tmp/ sync
No change needed
$ sqlite3 ./test.db "SELECT COUNT(*) from entries;"
168
$
```
