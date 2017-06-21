# squid-custom
This repository includes Dockerfile to build custom version of squid proxy.

## Changes on Squid
There is no retry-interval on connection error in upstream squid.<br>
In this version of squid, it will retry in every 10 seconds in case connection attempt failed.


## How to build it

```
docker build -t style95/squid:3.5.26-custom .
```

## How to run it

```
docker run -d -p 3128:3128 style95/squid:3.5.26-custom
```

## Warning

This is designed for special case.<br>
It will retry maximum 10 times with 10 seconds interval.<br>
So it will spent maximum 100 seconds to open connection to the backend server.

In normal case, it's not desirable to spent 100 seconds to open connection.<br>
Exponential back-off could be a good option, but that is not addressed in this version.
