FROM ubuntu:bionic
ENV DEBIAN_FRONTEND=noninteractive
MAINTAINER Christian Brandt <christian.jena@gmail.com>

RUN apt-get update && apt-get install -y \
        git \
        g++ \
        make \
        openjdk-8-jdk
        #openjdk-8-jre-headless \
        #ca-certificates-java \
        #openjdk-8-jdk && \
        #/usr/sbin/update-java-alternatives -s java-1.8.0-openjdk-amd64

RUN git clone https://github.com/marbl/canu.git && \
    cd canu/src && \
    make

ENV PATH /canu/Linux-amd64/bin/:$PATH
