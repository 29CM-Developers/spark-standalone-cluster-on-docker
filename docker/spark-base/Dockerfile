ARG spark_version
ARG hadoop_version

FROM bde2020/spark-base:${spark_version}-hadoop${hadoop_version}

# -- Installation Layer
RUN mkdir spark/credentials
COPY ./credentials spark/credentials
RUN curl https://storage.googleapis.com/hadoop-lib/gcs/gcs-connector-hadoop2-latest.jar -o spark/jars/gcs-connector-hadoop2-latest.jar && \
    echo "spark.hadoop.google.cloud.auth.service.account.enable       true" >> spark/conf/spark-defaults.conf && \
    echo "spark.hadoop.google.cloud.auth.service.account.json.keyfile credentials/29cm-credential.json" >> spark/conf/spark-defaults.conf

ENV SPARK_HOME /spark
ENV SPARK_MASTER_HOST spark-master
ENV SPARK_MASTER_PORT 7077
ENV PYSPARK_PYTHON python3

# -- Runtime

WORKDIR ${SPARK_HOME}