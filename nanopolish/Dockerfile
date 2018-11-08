FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN git clone --recursive https://github.com/jts/nanopolish
WORKDIR  /nanopolish/
RUN make
ENV PATH /nanopolish/:$PATH
