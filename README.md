# Cassandra Count Docker

This is a Docker image for counting rows in a Cassandra table. It uses the great [cassandra-count](https://github.com/brianmhess/cassandra-count) command line tool by [brianmhess](https://github.com/brianmhess).

Currently it only supports to set the host and port of the Cassandra instance as well as the table name to request and its corresponding keyspace. These parameters are set via environment variables. Usage from Docker is as follows:

````bash
docker pull soerenhenning/cassandra-count
docker run --rm --name cassandra-count -e "CASSANDRA_HOST=localhost" -e "CASSANDRA_PORT=9042" -e "KEYSPACE=my-keyspace" -e "TABLE=my-table" --network host soerenhenning/cassandra-count
````

The configuration for `--network` depends on the context your Cassandra instance is deployed in.

### Kubernetes

Usage in Kubernetes is straightforward:
````bash
kubectl run cassandra-count --rm --attach --restart=Never --image=soerenhenning/cassandra-count --env "CASSANDRA_HOST=cassandra" --env "CASSANDRA_PORT=9042" --env "KEYSPACE=my-keyspace" --env "TABLE=my-table"
````
