# Downloading base image
FROM ubuntu:14.04

MAINTAINER vckbansod12 <vckbansod12@gmail.com>

ENV es_jvm=2g

# Installing java
WORKDIR /opt/cs
ADD data/java/ java/
RUN update-alternatives --install /usr/bin/java java /opt/cs/java/jdk1.8.0_181/bin/java 100 && \
	update-alternatives --install /usr/bin/javac javac /opt/cs/java/jdk1.8.0_181/bin/javac 100 && \
	update-alternatives --config java && \
	update-alternatives --config javac && \
	update-alternatives --display java && \
	update-alternatives --display javac 

#creating user
RUN useradd -U -d /opt/cs -s /bin/bash elastic 

# Setting Up Elasticsearch
COPY data/elastic/ cs_IWP/elastic/
RUN chown -R elastic:elastic cs_IWP
USER elastic
RUN echo "export ES_HEAP_SIZE=${es_jvm}" >> /opt/cs/cs_IWP/elastic/elasticsearch-2.1.1/bin/elasticsearch

#Starting elasticsearch
WORKDIR /opt/cs/cs_IWP/elastic/elasticsearch-2.1.1/bin/
CMD [ "./elasticsearch" ] 

