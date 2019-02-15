# Downloading base image
FROM ubuntu:14.04
MAINTAINER vckbansod12 <vckbansod12@gmail.com>

WORKDIR /opt/cs


# Installing java
ADD data/java/ java/
RUN update-alternatives --install /usr/bin/java java /opt/cs/java/jdk1.8.0_181/bin/java 100 && \
	update-alternatives --install /usr/bin/javac javac /opt/cs/java/jdk1.8.0_181/bin/javac 100 && \
	update-alternatives --config java && \
	update-alternatives --config javac && \
	update-alternatives --display java && \
	update-alternatives --display javac

#creating user
RUN useradd -U -d /opt/cs -s /bin/bash orient
RUN usermod -aG sudo orient

# Setting Up Elasticsearch
COPY data/orientdb/ cs_IWP/orient/
RUN chown -R orient:orient cs_IWP
USER orient 


#Starting elasticsearch
WORKDIR /opt/cs/cs_IWP/orient/orientdb-community-2.2.22/bin/
CMD [ "./server.sh" ]   