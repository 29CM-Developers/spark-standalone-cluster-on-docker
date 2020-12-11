ARG spark_version
ARG hadoop_version
ARG spark_master_host="spark-master"
FROM spark-29cm-base:spark-${spark_version}-hadoop-${hadoop_version}
#FROM bde2020/spark-master:${spark_version}-hadoop${hadoop_version}

# -- Runtime Layer
#EXPOSE 8080 7077
ENV SPARK_MASTER_HOST ${spark_master_host:-spark-master}
CMD mkdir logs && \
    bin/spark-class org.apache.spark.deploy.master.Master >> logs/spark-master.out
