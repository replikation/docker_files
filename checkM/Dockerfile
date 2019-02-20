FROM ubuntu:bionic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
					 wget
RUN apt-get clean

RUN wget --no-check-certificate https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -b -p /conda
RUN rm -f Miniconda3-latest-Linux-x86_64.sh
ENV PATH /conda/bin:$PATH
RUN conda config --add channels bioconda

RUN conda install checkm-genome

# clean up
RUN apt-get clean && apt-get purge -y wget
