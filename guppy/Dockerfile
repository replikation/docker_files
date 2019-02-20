FROM ubuntu:xenial
MAINTAINER Christian Brandt <christian.jena@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get install -y — no-install-recommends \
    wget \
    lsb-release \
    apt-transport-https
RUN wget -O- https://mirror.oxfordnanoportal.com/apt/ont-repo.pub | apt-key add -
RUN PLATFORM=$(lsb_release -cs) && echo "deb http://mirror.oxfordnanoportal.com/apt ${PLATFORM}-stable non-free" | tee /etc/apt/sources.list.d/nanoporetech.sources.list
RUN apt-get update
RUN apt-get install -y ont-guppy-cpu
ENTRYPOINT ["guppy_basecaller"]
CMD ["-h"]

# clean up
RUN apt-get clean && apt-get remove wget lsb-release
