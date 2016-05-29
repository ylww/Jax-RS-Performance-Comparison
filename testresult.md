测试方式以及测试结果

> 因为都采用了基本的配置，因此本测试不具有参考意义

DO: 4 GB Memory节点

```bash
docker pull williamyeh/wrk&&docker run --rm williamyeh/wrk --version

#springboot
docker run --rm williamyeh/wrk -t16 -c1000 -d60s http://172.17.0.1:8080/hello

#jersey
docker run --rm williamyeh/wrk -t16 -c1000 -d30s http://172.17.0.1:8080/rest/hello
```


export JAVA_OPTS="-Xmx3g -Xms3g"

## springboot-undertow
```
root@docker-4gb-sfo1-01:~# docker run --rm williamyeh/wrk -t16 -c1000 -d60s http://172.17.0.1:8080/hello
Running 1m test @ http://172.17.0.1:8080/hello
  16 threads and 1000 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    93.44ms   61.97ms   2.00s    97.97%
    Req/Sec   682.16    123.73     1.43k    84.10%
  646584 requests in 1.00m, 93.11MB read
  Socket errors: connect 0, read 0, write 0, timeout 93
Requests/sec:  10759.66
Transfer/sec:      1.55MB
```
## springboot with tomcat

```
root@docker-4gb-sfo1-01:~# docker run --rm williamyeh/wrk -t16 -c1000 -d60s http://172.17.0.1:8080/hello
Running 1m test @ http://172.17.0.1:8080/hello
  16 threads and 1000 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   129.91ms   81.89ms   1.17s    81.53%
    Req/Sec   502.26     97.33     1.18k    73.77%
  477851 requests in 1.00m, 70.26MB read
Requests/sec:   7955.36
Transfer/sec:      1.17MB
```

## jersey
```
root@docker-4gb-sfo1-01:~# docker run --rm williamyeh/wrk -t16 -c1000 -d60s http://172.17.0.1:8080/rest/hello
Running 1m test @ http://172.17.0.1:8080/rest/hello
  16 threads and 1000 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   113.29ms   21.21ms 315.63ms   86.04%
    Req/Sec   546.56    101.42     1.25k    81.55%
  521657 requests in 1.00m, 56.25MB read
Requests/sec:   8680.20
Transfer/sec:      0.94MB
```
