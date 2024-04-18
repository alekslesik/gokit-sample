### Start CockroachDB cluster

cockroach start \
--certs-dir=certs \
--store=ordersdb-1 \
--listen-addr=localhost:26257 \
--http-addr=localhost:8080 \
--join=localhost:26257,localhost:26258,localhost:26259

cockroach start \
--certs-dir=certs \
--store=ordersdb-2 \
--listen-addr=localhost:26258 \
--http-addr=localhost:8081 \
--join=localhost:26257,localhost:26258,localhost:26259

cockroach start \
--certs-dir=certs \
--store=ordersdb-3 \
--listen-addr=localhost:26259 \
--http-addr=localhost:8082 \
--join=localhost:26257,localhost:26258,localhost:26259

### Start Zipkin in Docker
docker run -d -p 9411:9411 openzipkin/zipkin


ps -ef | grep cockroach | grep -v grep
kill -TERM 4482