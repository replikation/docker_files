FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
# install conda
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -b -p /conda
RUN rm -f Miniconda3-latest-Linux-x86_64.sh
ENV PATH /conda/bin:$PATH
RUN conda config --add channels bioconda
RUN conda config --add channels conda-forge
RUN conda install abricate
RUN abricate --check
ENTRYPOINT ["abricate"]
