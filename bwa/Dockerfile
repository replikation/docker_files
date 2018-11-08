FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN wget https://github.com/lh3/bwa/archive/master.zip
RUN unzip master.zip; rm master.zip
WORKDIR  /bwa-master/
RUN make
ENV PATH /bwa-master/:$PATH
