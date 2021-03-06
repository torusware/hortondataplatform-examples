# Hortonworks Data Platform

## Automated Install with Ambari 

* Launch the container running Ambari Server and Ambari Agent
```
docker run  -p 8080:8080 --rm -ti --privileged --name hdp -h hdp torusware/hortondataplatform-examples
```
* You can also deploy a cluster automatically using Ambari blueprints
```
docker run -e BLUEPRINT_URL=<ambari blueprint url> -e CLUSTER_TEMPLATE_URL=<cluster template url> -p 8080:8080 --rm -ti --privileged -h hdp  torusware/hortondataplatform-examples
```
* Open your browser and go to http://localhost:8080
* Access a running container through ssh
```
$ sshpass -p 'torus' ssh root@<container IP>
```

## Spark examples

### Configure environment

- Set up the Hadoop ecosystem
  1. Pull container `docker pull torusware/hortondataplatform-examples`
  2. Launch container as above: `docker run  -p 8080:8080 --rm -ti --privileged --name hdp -h hdp torusware/hortondataplatform-examples`
  4. Access http://localhost:8080 from your host browser
  5. Login: admin/admin
  6. Launch install wizard with the hostname and ssh key set in the configuration step
  7. Install services: HDFS, YARN, Ambari Metrics and Spark

- Run examples within the container shell

### Run examples

- [TwitterPopularTags](https://github.com/apache/spark/blob/master/examples/src/main/scala/org/apache/spark/examples/streaming/TwitterPopularTags.scala)

  ```
  spark-submit --class org.apache.spark.examples.streaming.TwitterPopularTags \           
  /usr/hdp/current/spark-client/lib/spark-examples-1.5.2.2.3.4.0-3485-hadoop2.7.1.2.3.4.0-3485.jar \
  <consumer key> <consumer secret> <access token> <access token secret>  [<filters>]
  ```
