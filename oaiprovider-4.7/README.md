Run [Fedora 4 with OAI Provider](https://github.com//ualbertalib/fcrepo4-oaiprovider) using docker 

## How to use this image
Pull down image: `docker pull ualbertalib/docker-fcrepo4:oaiprovider-4.7`

Run the image, mapping your ports to your localmachine: `docker run -p 8080:8080 ualbertalib/docker-fcrepo4:oaiprovider-4.7`

Open brower and navigate to `http://localhost:8080/fcrepo/rest/`

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
