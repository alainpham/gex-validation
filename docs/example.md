Mimirtool


```

mimirtool bucket-validation --bucket-config="-backend=s3 -s3.bucket-name=sandbox -s3.endpoint=minio.work.lan:443 -s3.access-key-id=admin -s3.insecure=false -s3.secret-access-key=password"

mimirtool bucket-validation --bucket-config="-backend=s3\
 -s3.bucket-name=sandbox\
 -s3.endpoint=minio.work.lan:443\
 -s3.access-key-id=admin\
 -s3.insecure=false\
 -s3.secret-access-key=password"
```

Resulsts

```

level=info phase="creating test objects" completed=0 total=2000
level=info phase="creating test objects" completed=100 total=2000
level=info phase="creating test objects" completed=200 total=2000
level=info phase="creating test objects" completed=300 total=2000
level=info phase="creating test objects" completed=400 total=2000
level=info phase="creating test objects" completed=500 total=2000
level=info phase="creating test objects" completed=600 total=2000
level=info phase="creating test objects" completed=700 total=2000
level=info phase="creating test objects" completed=800 total=2000
level=info phase="creating test objects" completed=900 total=2000
level=info phase="creating test objects" completed=1000 total=2000
level=info phase="creating test objects" completed=1100 total=2000
level=info phase="creating test objects" completed=1200 total=2000
level=info phase="creating test objects" completed=1300 total=2000
level=info phase="creating test objects" completed=1400 total=2000
level=info phase="creating test objects" completed=1500 total=2000
level=info phase="creating test objects" completed=1600 total=2000
level=info phase="creating test objects" completed=1700 total=2000
level=info phase="creating test objects" completed=1800 total=2000
level=info phase="creating test objects" completed=1900 total=2000
level=info phase="creating test objects" completed=2000 total=2000
level=info phase="overwriting test objects" completed=0 total=2000
level=info phase="overwriting test objects" completed=100 total=2000
level=info phase="overwriting test objects" completed=200 total=2000
level=info phase="overwriting test objects" completed=300 total=2000
level=info phase="overwriting test objects" completed=400 total=2000
level=info phase="overwriting test objects" completed=500 total=2000
level=info phase="overwriting test objects" completed=600 total=2000
level=info phase="overwriting test objects" completed=700 total=2000
level=info phase="overwriting test objects" completed=800 total=2000
level=info phase="overwriting test objects" completed=900 total=2000
level=info phase="overwriting test objects" completed=1000 total=2000
level=info phase="overwriting test objects" completed=1100 total=2000
level=info phase="overwriting test objects" completed=1200 total=2000
level=info phase="overwriting test objects" completed=1300 total=2000
level=info phase="overwriting test objects" completed=1400 total=2000
level=info phase="overwriting test objects" completed=1500 total=2000
level=info phase="overwriting test objects" completed=1600 total=2000
level=info phase="overwriting test objects" completed=1700 total=2000
level=info phase="overwriting test objects" completed=1800 total=2000
level=info phase="overwriting test objects" completed=1900 total=2000
level=info phase="overwriting test objects" completed=2000 total=2000
level=info phase="listing test objects"
level=info phase="validating test objects" completed=0 total=2000
level=info phase="validating test objects" completed=100 total=2000
level=info phase="validating test objects" completed=200 total=2000
level=info phase="validating test objects" completed=300 total=2000
level=info phase="validating test objects" completed=400 total=2000
level=info phase="validating test objects" completed=500 total=2000
level=info phase="validating test objects" completed=600 total=2000
level=info phase="validating test objects" completed=700 total=2000
level=info phase="validating test objects" completed=800 total=2000
level=info phase="validating test objects" completed=900 total=2000
level=info phase="validating test objects" completed=1000 total=2000
level=info phase="validating test objects" completed=1100 total=2000
level=info phase="validating test objects" completed=1200 total=2000
level=info phase="validating test objects" completed=1300 total=2000
level=info phase="validating test objects" completed=1400 total=2000
level=info phase="validating test objects" completed=1500 total=2000
level=info phase="validating test objects" completed=1600 total=2000
level=info phase="validating test objects" completed=1700 total=2000
level=info phase="validating test objects" completed=1800 total=2000
level=info phase="validating test objects" completed=1900 total=2000
level=info phase="validating test objects" completed=2000 total=2000
level=info phase="deleting test objects" completed=0 total=2000
level=info phase="deleting test objects" completed=100 total=2000
level=info phase="deleting test objects" completed=200 total=2000
level=info phase="deleting test objects" completed=300 total=2000
level=info phase="deleting test objects" completed=400 total=2000
level=info phase="deleting test objects" completed=500 total=2000
level=info phase="deleting test objects" completed=600 total=2000
level=info phase="deleting test objects" completed=700 total=2000
level=info phase="deleting test objects" completed=800 total=2000
level=info phase="deleting test objects" completed=900 total=2000
level=info phase="deleting test objects" completed=1000 total=2000
level=info phase="deleting test objects" completed=1100 total=2000
level=info phase="deleting test objects" completed=1200 total=2000
level=info phase="deleting test objects" completed=1300 total=2000
level=info phase="deleting test objects" completed=1400 total=2000
level=info phase="deleting test objects" completed=1500 total=2000
level=info phase="deleting test objects" completed=1600 total=2000
level=info phase="deleting test objects" completed=1700 total=2000
level=info phase="deleting test objects" completed=1800 total=2000
level=info phase="deleting test objects" completed=1900 total=2000
level=info phase="deleting test objects" completed=2000 total=2000
level=info testrun_successful=1
```

Warp test

```
warp mixed --obj.randsize --obj.size=1500KiB --host=minio.work.lan:443 --tls --access-key=admin --secret-key=password --autoterm --bucket=warp-test
```

Results

```
Mixed operations.
Operation: DELETE, 10%, Concurrency: 20, Ran 36s.
 * Throughput: 315.37 obj/s

Operation: GET, 45%, Concurrency: 20, Ran 36s.
 * Throughput: 372.67 MiB/s, 1419.58 obj/s

Operation: PUT, 15%, Concurrency: 20, Ran 36s.
 * Throughput: 125.23 MiB/s, 473.25 obj/s

Operation: STAT, 30%, Concurrency: 20, Ran 36s.
 * Throughput: 946.50 obj/s

Cluster Total: 497.88 MiB/s, 3154.48 obj/s over 36s.
```