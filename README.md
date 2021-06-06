# docker-solr with no volumes to create custom solr cores via Dockerfile

This repo is directly forked from the official docker-solr repo

### Use docker image on docker-hub

if you want to create a simple core named **simple.core**

```dockerfile
FROM sebinpj/solr:8.4

RUN solr start \
 && solr create -c simple.core \

CMD ["solr-foreground"]
```

If you want to create a core with custom schema 

```dockerfile
FROM sebinpj/solr:8.4

RUN solr start \
 && solr create -c schema.core \
 && solr stop
 
COPY managed-schema /var/solr/data/schema.core/conf/managed-schema

CMD ["solr-foreground"]
```

### Build images on local machine

to build a image run 

```shell
tools\build.sh <solr_version> # based on directory
```

Make sure all files are under LF file endings when creating image
