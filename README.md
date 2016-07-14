dwhois
======

Client and worker for a database of WHOIS records accessed via HTTP.
Has an optional MongoDB-backed result cache.

Configuration
-------------

Create `/etc/dwhois.conf` or `~/.dwhois.conf`.  Set whatever options you need to from:

```
[dwhois]
user=your username
password=your password
average_time=time per domain in seconds
url=https://path/to/api/version/
request_timeout=10

[cache]
use_cache=True
url=mongodb://url_to_mongodb/ (optional, defaults to localhost)
db=dwhois
collection=dwhois
```

Querying
--------

```
usage: dwhois [-h] [--json] [--files [FILES [FILES ...]]] [--check] [--submit]
              [domains [domains ...]]

positional arguments:
  domains               list of domains

optional arguments:
  -h, --help            show this help message and exit
  --json, -j            json output
  --files [FILES [FILES ...]], -f [FILES [FILES ...]]
                        file with domains
  --check, -c           check instead of get
  --submit, -s          submit domains
```

User Account Info
-----------------

```
usage: dwhois-user [-h] user

positional arguments:
  user        user to query

optional arguments:
  -h, --help  show this help message and exit
```

Worker Process
--------------

Run `dwhois-worker` in screen or with runit.

Or set pidfile in /etc/dwhois.conf to a sensible value and run `dwhois-worker -d`

Or use the init script suitable to your distribution from the scripts directory.
