# S3 Resource R

[![Build Status](https://travis-ci.com/obiba/s3.resourcer.svg?branch=master)](https://travis-ci.com/obiba/s3.resourcer)
[![CRAN_Status_Badge](http://www.r-pkg.org/badges/version/s3.resourcer)](https://cran.r-project.org/package=s3.resourcer)

The `s3.resourcer` package is for accessing a file stored in the AWS S3 system or in a HTTP S3 compatible object store such as [minio](https://min.io/). It makes use of the [aws.s3](https://github.com/cloudyr/aws.s3) R package and of [sparklyr](https://spark.rstudio.com/) when the S3 file store is accessed through Apache Spark.

### S3 File Getter

The resource is a file which location is described by a URL with scheme `s3` (Amazon Web Services S3 file store) or `s3+http` or `s3+https` (Minio implementation of the S3 API over HTTP). To authenticate, the AWS/HTTP S3 key is the resource's identity and the AWS/HTTP S3 secret is the resource's secret.

For instance this is a valid resource object that can be accessed by the `S3FileResourceGetter`:

```
library(s3.resourcer)
res <- resourcer::newResource(url="s3://my_bucket/mtcars.Rdata", format = "data.frame")
client <- resourcer::newResourceClient(res)
client$asDataFrame()
```

or

```
library(s3.resourcer)
res <- resourcer::newResource(url="s3+https://minio.example.org/test/mtcars.Rdata", format = "data.frame")
client <- resourcer::newResourceClient(res)
client$asDataFrame()
```
