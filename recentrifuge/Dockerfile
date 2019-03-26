FROM ubuntu:bionic
MAINTAINER Christian Brandt <christian.jena@gmail.com>

# python3 & pip3
RUN apt-get update --fix-missing && apt-get install -y \
					 locales \
					 python3 \
					 python3-pip \
					 python3-setuptools

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# ENV PYTHONIOENCODING=utf-8

# install recentrifuge
RUN pip3 install recentrifuge
RUN pip3 install pandas openpyxl xlrd matplotlib

# install database
RUN mkdir -p /database/ncbi_node
RUN retaxdump -n /database/ncbi_node

RUN apt-get clean
ENTRYPOINT ["rcf"]
