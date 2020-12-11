ARG spark_version
ARG hadoop_version
FROM spark-29cm-base:spark-${spark_version}-hadoop-${hadoop_version}

# -- Runtime Layer
ENV SPARK_MASTER_HOST ${spark_master_host:-spark-master}
EXPOSE 8081
CMD mkdir logs && \
    bin/spark-class org.apache.spark.deploy.worker.Worker spark://${SPARK_MASTER_HOST}:${SPARK_MASTER_PORT} >> logs/spark-worker.out
