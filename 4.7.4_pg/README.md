# docker-fcrepo4/4.7.4_pg
docker-compose for Fedora 4.7.4 with Postgres DB configuration

# Initialize Postgres DB

```shell
$ docker-compose --env-file .env_prod up -d postgres
$ docker cp ./fcrepo.sql.gz postgres:/tmp # copy fcrepo database dump to postgres container
$ docker exec -it postgres /bin/bash      # run bash shell on the container
$ cd /tmp
$ gzip -d fcrepo.sql.gz                   # extract the database dump
$ su - postgres
$ psql
$ postgres=# create database fcrepo;      # create fcrepo database
$ postgres=# \q
$ psql fcrepo < fcrepo.sql                # import data to the database
$ exit                                    # exit from postgres user
$ exit                                    # exit from postgres container
```

# Start fcrepo service
Create .env_prod from .env_dev and modify FCREPO_HOME pointing to Fedora data directory

```shell
# .env_prod
JAVA_OPTS=-Dfcrepo.log=DEBUG -Dfcrepo.log.jcr=DEBUG -Dfcrepo.log.directory=$CATALINA_HOME/logs -Dfcrepo.log.maxHistory=10 -Dfcrepo.log.totalSizeCap=100000 -Djava.awt.headless=true -Dfile.encoding=UTF-8 -server -Duser.timezone=America/Edmonton -Dfile.encoding=UTF8 -Dfcrepo.modeshape.configuration=classpath:/config/jdbc-postgresql/repository.json -Dfcrepo.postgresql.username=postgres -Dfcrepo.postgresql.password=postgres -Dfcrepo.postgresql.host=postgres -Dfcrepo.postgresql.port=5432 -Djava.xml.transform.TransformerFactory=net.sf.saxon.TransformerFactoryImpl -Dfcrepo.triplestore.activemq.broker=localhost:61616 -Dfcrepo.home=/fedora_data

FCREPO_HOME=/media/pcharoen/WDMyBook/fedora_data
```

```shell
$ docker-compose --env-file=.env_prod up -d fcrepo
```

# Stop services
```shell
$ docker-compose --env-file=.env_prod stop
```

# Start Fedora 4.7.4 server
```shell
$ docker-compose --env-file=.env_prod start
```