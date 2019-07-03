FROM debian:stretch

SHELL ["/bin/bash", "-c"]
RUN apt-get update && apt-get upgrade -y
RUN apt-get install default-jdk scala curl vim -y

RUN curl -O https://archive.apache.org/dist/spark/spark-2.2.1/spark-2.2.1-bin-hadoop2.7.tgz
RUN tar -xvf spark-2.2.1-bin-hadoop2.7.tgz
RUN mv spark-2.2.1-bin-hadoop2.7/ /opt/spark
RUN cp /opt/spark/bin/spark-shell /usr/bin

RUN useradd -ms /bin/bash spark
USER spark
RUN mkdir /home/spark/scripts
WORKDIR /home/spark

RUN echo "export SPARK_HOME=/opt/spark" >> ~/.bashrc
RUN echo "export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin" >> ~/.bashrc

