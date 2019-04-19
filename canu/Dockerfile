FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN git clone https://github.com/marbl/canu.git
WORKDIR /canu/src
RUN make
ENV PATH /canu/Linux-amd64/bin:$PATH
