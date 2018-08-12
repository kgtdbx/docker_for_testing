`docker_for_testing` – Used to build a pgsentinel testing docker image
=============================================================

Introduction
------------

Dockerfile used to provision a testing docker image, it:

 * downloads the postgresql source code (version of your choice)
 * compiles and installs it
 * downloads the pgsentinel extension
 * compiles and installs it
 * compiles and installs the pg_stat_statements extension

Warning
------------

For testing pgsentinel only, 100% stateless 

Usage
------------

3 arguments can be used:

 * PG_VERSION (default: 10.5)
 * PG_ASH_SAMPLING (default: 1)
 * PG_ASH_MAX_ENTRIES (default: 10000)

Example to build an image:

```
docker build -t pgsentinel-testing -f Dockerfile-pgsentinel-testing --build-arg PG_VERSION=11beta3 --force-rm=true --no-cache=true .
```

Once done, example to launch a container:

```
docker run -d -p 5432:5432 --name pgsentinel pgsentinel-testing
```

Author
-------
 
 * Bertrand Drouvot <bdrouvot@gmail.com>,
   Metz, France [!['test'](https://www.pgsentinel.com/images/twitter.png)](https://twitter.com/BertrandDrouvot) [!['test'](https://www.pgsentinel.com/images/linkedin.png)](https://www.linkedin.com/in/bdrouvot/)
