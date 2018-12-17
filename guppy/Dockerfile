FROM ubuntu:xenial
MAINTAINER Christian <christian.jena@gmail.com>
RUN apt-get update
RUN apt-get install -y 	wget
RUN wget https://mirror.oxfordnanoportal.com/software/analysis/ont-guppy-cpu_2.1.3_linux64.tar.gz
RUN wget -O- https://mirror.oxfordnanoportal.com/apt/ont-repo.pub | apt-key add -
RUN echo "deb http://mirror.oxfordnanoportal.com/apt xenial-stable non-free" | tee /etc/apt/sources.list.d/nanoporetech.sources.list
RUN apt-get install -y apt-transport-https
RUN apt-get update
RUN apt-get install -yf ont-guppy-cpu
ENTRYPOINT ["guppy_basecaller"]
CMD ["-h"]
