FROM openjdk:8-alpine
RUN apk --update add wget tar bash
# Spark Link 2.2.1 
# https://archive.apache.org/dist/spark/spark-2.2.1/
RUN wget https://archive.apache.org/dist/spark/spark-2.2.1/spark-2.2.1-bin-hadoop2.7.tgz
RUN tar -xzf spark-2.2.1-bin-hadoop2.7.tgz && \
	mv spark-2.2.1-bin-hadoop2.7 /spark && \
	rm spark-2.2.1-bin-hadoop2.7.tgz
COPY start-worker.sh /start-worker.sh
COPY start-master.sh /start-master.sh

# For python specific setup
RUN apk add python3
RUN echo "alias python=python3" >> ~/.bashrc
ENV PYSPARK_PYTHON=/usr/bin/python3