# Grafana Enterprise Metrics - Logs - Traces Validation

- [Grafana Enterprise Metrics - Logs - Traces Validation](#grafana-enterprise-metrics---logs---traces-validation)
  - [Feature Validation](#feature-validation)
    - [Download \& test mimirtool](#download--test-mimirtool)
    - [Test bucket functionality](#test-bucket-functionality)
  - [Performance validation](#performance-validation)


For on premise GEM GEL GET installations, object storage performance can vary widely based on the underlying hardware & solutions used.

This document describes how to validate the object store in terms of features and performance to have a smooth experience on GEM GEL and GET.

## Feature Validation

### Download & test mimirtool

Release page :

[https://github.com/grafana/mimir/releases](https://github.com/grafana/mimir/releases)

Direct links : 

* Linux AMD 64 : [https://github.com/grafana/mimir/releases/download/mimir-2.6.0/mimirtool-linux-amd64](https://github.com/grafana/mimir/releases/download/mimir-2.6.0/mimirtool-linux-amd64)
* Windows AMD 64: [https://github.com/grafana/mimir/releases/download/mimir-2.6.0/mimirtool-windows-amd64.exe](https://github.com/grafana/mimir/releases/download/mimir-2.6.0/mimirtool-windows-amd64.exe)


```
sudo curl -L -o /usr/local/bin/mimirtool https://github.com/grafana/mimir/releases/download/mimir-2.6.0/mimirtool-linux-amd64 

sudo chmod 755 /usr/local/bin/mimirtool
```

```
mimirtool version

### EXAMPLE RESULTS ###

Mimirtool, version 2.4.0 (branch: release-2.4, revision: 32137ee2c)
  go version:       go1.19.2
  platform:         linux/amd64
checking latest version... You are on the latest version
```

### Test bucket functionality

Run the following command by changing the input parameters to your environment. You should use a test bucket without any data in it.

**/!\ Warning the bucket will be erased. make sure it is a bucket without critical data.**

```
mimirtool bucket-validation --bucket-config="-backend=s3 -s3.bucket-name=sandbox -s3.endpoint=minio.work.lan:443 -s3.access-key-id=admin -s3.insecure=false -s3.secret-access-key=password"
```

Example results

```

level=info phase="creating test objects" completed=0 total=2000
…
…
level=info phase="creating test objects" completed=100 total=2000
level=info phase="deleting test objects" completed=2000 total=2000
level=info testrun_successful=1

```

Copy the command used and output here :

```
YOUR RESULT
```


## Performance validation


To benchmark S3-compliant object stores, we’ll use MinIO’s warp benchmarking tool. 

Release page: 

[https://github.com/minio/warp/releases](https://github.com/minio/warp/releases)


Direct download link : 

[https://github.com/minio/warp/releases/download/v0.6.6/warp_0.6.6_Linux_x86_64.tar.gz](https://github.com/minio/warp/releases/download/v0.6.6/warp_0.6.6_Linux_x86_64.tar.gz)

```
curl -L -o  /tmp/warp.tar.gz https://github.com/minio/warp/releases/download/v0.6.6/warp_0.6.6_Linux_x86_64.tar.gz

tar -xzvf /tmp/warp.tar.gz -C /tmp/  warp 

sudo mv /tmp/warp /usr/local/bin/
```

Run the following command by changing the parameters to your needs. 

**/!\ Warning the bucket will be erased. make sure it is a bucket without critical data.**

```
warp mixed --obj.randsize --obj.size=1500KiB --host=YOUR_S3_HOST:PORT --access-key=YOUR_ACCESS_KEY --secret-key=YOUR_SECRET --tls --autoterm --bucket=YOUR_BUCKET
```

Example Raw output:

```
Throughput 35.9 objects/s within 7.500000% for 17.08s. Assuming stability. Terminating benchmark.
warp: Benchmark data written to "warp-mixed-2022-01-26[132248]-7mjQ.csv.zst"
Mixed operations.
Operation: DELETE, 10%, Concurrency: 20, Ran 1m1s.
 * Throughput: 11.42 obj/s

Operation: GET, 45%, Concurrency: 20, Ran 1m1s.
 * Throughput: 511.93 MiB/s, 51.19 obj/s

Operation: PUT, 15%, Concurrency: 20, Ran 1m1s.
 * Throughput: 170.56 MiB/s, 17.06 obj/s

Operation: STAT, 30%, Concurrency: 20, Ran 1m1s.
 * Throughput: 34.21 obj/s

Cluster Total: 681.02 MiB/s, 113.69 obj/s over 1m2s.

```


Copy the command used and output here :

```
YOUR RESULT
```
