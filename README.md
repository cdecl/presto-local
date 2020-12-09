# presto-local

## Install 

```sh
# presto & catalog config 
$ git clone https://github.com/cdecl/presto-local.git
$ cd presto-local

# download presto-server 
$ curl -O https://repo1.maven.org/maven2/com/facebook/presto/presto-server/0.244.1/presto-server-0.244.1.tar.gz
$ tar zxvf presto-server-0.244.1.tar.gz
$ mv presto-server-0.244.1 /usr/local/

# copy presto & catalog config 
$ cp -r ./etc/ /usr/local/presto-server-0.244.1/
```

## Start 

### Prerequisites
- Make bucket MinIO : `s3://catalog/`

```config
# etc/hive.properties
...
hive.metastore.catalog.dir=s3://catalog/
...
```

```sh
# mc config host add minio ${S3_ENDPOINT} ${AWS_ACCESS_KEY} ${AWS_SECRET_KEY}
$ mc mb minio/catalog
```

### Run

```sh
$ cd presto-server-0.244.1.tar.gz

# service start
$ bin/launcher start
```
