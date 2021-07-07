# docker-fcrepo4
[![](https://images.microbadger.com/badges/image/ualbertalib/docker-fcrepo4.svg)](https://microbadger.com/images/ualbertalib/docker-fcrepo4 "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/ualbertalib/docker-fcrepo4.svg)](https://microbadger.com/images/ualbertalib/docker-fcrepo4 "Get your own version badge on microbadger.com")
[![Build Status](https://travis-ci.org/ualbertalib/docker-fcrepo4.svg?branch=master)](https://travis-ci.org/ualbertalib/docker-fcrepo4)

Run [Fedora 4](https://github.com/fcrepo4/fcrepo4) using docker 

## How to use this image
Pull down image: `docker pull ualbertalib/docker-fcrepo4`

Run the image, mapping your ports to your localmachine: `docker run -p 8080:8080 ualbertalib/docker-fcrepo4`

Open brower and navigate to `http://localhost:8080/fcrepo/rest/`
