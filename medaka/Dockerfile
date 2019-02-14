FROM ubuntu:xenial
ENV DEBIAN_FRONTEND=noninteractive
MAINTAINER Christian Brandt <christian.jena@gmail.com>

RUN apt-get update && apt-get install -y --no-install-recommends \
					 python3 \
					 python3-pip \
					 python3-setuptools
RUN pip3 install --upgrade pip
RUN pip3 install medaka
RUN apt-get clean
ENTRYPOINT ["medaka"]
