# docker-fcrepo4:4.2

## Start Docker
```shell
$ docker pull ualbertalib/docker-fcrepo4:4.2
$ docker run --name fcrepo-4.2 -d -v ~/fcrepo4-data:/fcrepo4-data -p 8080:8080 ualbertalib/docker-fcrepo4:4.2
```

## Stop Docker
```shell
$ docker stop fcrepo-4.2
$ docker container rm fcrepo-4.2
```