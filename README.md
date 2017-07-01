# squid-custom
This repository includes Dockerfile to build custom version of squid proxy.

## Available tags

There is only one tag.

* `latest`
* `3.5.26-p1`

## Changes on Squid
There is no retry-interval on connection error in upstream squid.
In this version of squid, it will retry in every 10 seconds in case connection attempt failed.


## How to build it

```
docker build -t style95/squid:3.5.26-p1 .
```

## How to run it

```
docker run -d -p 3128:3128 style95/squid:3.5.26-p1
```

## Warning

This is designed for a very special case.
It will retry maximum 10 times with 10 seconds interval.
So it will spent maximum 100 seconds to open connection to the backend server.

In normal case, it's not desirable to spent 100 seconds to open connection.
Exponential back-off could be a good option, but that is not addressed in this version.
