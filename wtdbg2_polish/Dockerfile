FROM ubuntu:bionic
ENV DEBIAN_FRONTEND=noninteractive
MAINTAINER Christian Brandt <christian.jena@gmail.com>

RUN apt-get update && apt-get install -y --no-install-recommends \
           git \
					 make \
					 wget \
					 g++ \
           bzip2 \
           lbzip2 \
           libbz2-dev \
           liblzma-dev \
           zlib1g-dev
RUN apt-get clean

# install samtools
RUN wget --no-check-certificate https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2 \
    && tar xjf samtools*.tar.bz2 && rm samtools*.tar.bz2 \
    && mv /samtools-*/ /samtools/
RUN cd  /samtools/ \
    && ./configure --without-curses \
    && make && make install
# wtdbg2
RUN git clone -c http.sslVerify=false https://github.com/ruanjue/wtdbg2.git \
    && cd wtdbg2/ && make
ENV PATH /wtdbg2/:$PATH
# minimap2
RUN git clone -c http.sslVerify=false https://github.com/lh3/minimap2 \
    && cd minimap2 && make
ENV PATH /minimap2/:$PATH

# clean up
RUN apt-get clean && apt autoremove && apt-get purge -y wget git make
