FROM ubuntu:bionic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
					 wget
RUN apt-get clean

RUN wget --no-check-certificate https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -b -p /conda \
 		&& rm -f Miniconda3-latest-Linux-x86_64.sh
ENV PATH /conda/bin:$PATH
RUN conda config --add channels bioconda
RUN conda install checkm-genome

#download database
RUN wget --no-check-certificate https://data.ace.uq.edu.au/public/CheckM_databases/checkm_data_2015_01_16.tar.gz
RUN mkdir -p /checkm_database \
		&& tar -xzf checkm_data_2015_01_16.tar.gz -C /checkm_database \
		&& rm -rf checkm_data_2015_01_16.tar.gz
RUN echo /checkm_database | checkm data setRoot /checkm_database
ENTRYPOINT ["checkm"]

# clean up
RUN apt-get clean && apt-get purge -y wget
