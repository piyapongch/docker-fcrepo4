# Fedora 4.7.4 with OAI Provider

## Build docker
```shell
$ docker build -t pcharoen/fcrepo:4.7.4.t1 .
```

## Push to dockerhub
```shell
$ docker login
$ docker push pcharoen/fcrepo:4.7.4.t1
```
## Run 
```shell
$ docker-compose up -d
```

## UI
```shell
http://localhost:8080/fcrepo/rest/
```

## Ingest Sample Data
```shell
TODO: add sample data and ingest commands
```

In order to get some results, a couple of objects can be created:

```bash
#> curl -X POST http://localhost:8080/fcrepo/rest -H "Slug:foo"
#> curl -X POST http://localhost:8080/fcrepo/rest -H "Slug:bar"
```

Try the various responses from the oai provider:

```bash
#> curl http://localhost:8080/fcrepo/rest/oai?verb=ListMetadataFormats
#> curl "http://localhost:8080/fcrepo/rest/oai?verb=GetRecord&identifier=MyObject&metadataPrefix=oai_dc"
#> curl "http://localhost:8080/fcrepo/rest/oai?verb=ListRecords&metadataPrefix=oai_dc"
#> curl "http://localhost:8080/fcrepo/rest/oai?verb=ListIdentifiers&metadataPrefix=oai_dc"
#> curl "http://localhost:8080/fcrepo/rest/oai?verb=ListSets"
#> curl "http://localhost:8080/fcrepo/rest/oai?verb=ListIdentifiers&metadataPrefix=oai_dc&set=MyOAISet"
```
