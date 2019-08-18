# Spark Version
2.2.1 with hadoop 2.7

# How was this setup created ?
By following https://towardsdatascience.com/a-journey-into-big-data-with-apache-spark-part-1-5dfcc2bccdd2

All thanks to [Ashley Broadley](https://towardsdatascience.com/@ls12styler) for the article

# How to run this setup ? 
1. `Build image`: `docker build -t indiansher/spark .`
2. `Start Everything (with 2 workers)`: `docker-compose up --scale spark-worker=2`

# Check Status 
Browse to http://localhost:8080 and see the WebUi for the cluster

# Run a job

1. `docker run --rm -it --network apache-spark-image_spark-network indiansher/spark:latest /bin/bash`
	(If you get incorrect network name or any network related issues, Inspect the running containers using `docker container inspect <container-id> | grep NetworkMode` and get the network name from there. Use this network name in the above command)
2. `/spark/bin/spark-submit --master spark://spark-master:7077 --class org.apache.spark.examples.SparkPi /spark/examples/jars/spark-examples_2.11-2.2.1.jar 1000`
3. To run the same job without using the workers created above, just remove the master argument

## Python Jobs

1. `/spark/bin/spark-submit --master spark://spark-master:7077 /spark/examples/src/main/python/pi.py 1000`