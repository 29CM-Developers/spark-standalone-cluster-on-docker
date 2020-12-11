ARG spark_version
ARG hadoop_version
FROM spark-29cm-base:spark-${spark_version}-hadoop-${hadoop_version}
#FROM bde2020/spark-worker:${spark_version}-hadoop${hadoop_version}

# -- Installation Layer
#WORKDIR /spark
#
#RUN mkdir credentials
#COPY ./credentials credentials
#RUN curl https://storage.googleapis.com/hadoop-lib/gcs/gcs-connector-hadoop2-latest.jar -o jars/gcs-connector-hadoop2-latest.jar && \
#    echo "spark.hadoop.google.cloud.auth.service.account.enable       true" >> conf/spark-defaults.conf && \
#    echo "spark.hadoop.google.cloud.auth.service.account.json.keyfile credentials/29cm-credential.json" >> conf/spark-defaults.conf

#ENV SPARK_HOME /spark
#ENV SPARK_MASTER_HOST spark-master
#ENV SPARK_MASTER_PORT 7077
#ENV PYSPARK_PYTHON python3

# -- Runtime Layer
ENV SPARK_MASTER_HOST ${spark_master_host:-spark-master}
EXPOSE 8081
CMD mkdir logs && \
    bin/spark-class org.apache.spark.deploy.worker.Worker spark://${SPARK_MASTER_HOST}:${SPARK_MASTER_PORT} >> logs/spark-worker.out
