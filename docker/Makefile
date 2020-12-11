ifeq ($(SPARK_VERSION),)
  $(error SPARK_VERSION is not set)
endif

ifeq ($(HADOOP_VERSION),)
  $(error HADOOP_VERSION is not set)
endif

build-base-image:
	docker build --build-arg spark_version=$(SPARK_VERSION) \
				 --build-arg hadoop_version=$(HADOOP_VERSION) \
				 -t spark-29cm-base:spark-$(SPARK_VERSION)-hadoop-$(HADOOP_VERSION) \
				 -f docker/spark-base/Dockerfile  .

build-master-image:
	docker build --build-arg spark_version=$(SPARK_VERSION) \
				 --build-arg hadoop_version=$(HADOOP_VERSION) \
				 -t spark-29cm-master:spark-$(SPARK_VERSION)-hadoop-$(HADOOP_VERSION) \
				 -f docker/spark-master/Dockerfile  .

build-worker-image:
	docker build --build-arg spark_version=$(SPARK_VERSION) \
				 --build-arg hadoop_version=$(HADOOP_VERSION) \
				 -t spark-29cm-worker:spark-$(SPARK_VERSION)-hadoop-$(HADOOP_VERSION) \
				 -f docker/spark-worker/Dockerfile  .

build-all: build-base-image build-master-image build-worker-image