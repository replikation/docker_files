FROM replikation/debian_python3
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN wget https://github.com/ruanjue/wtdbg2/archive/master.zip
RUN unzip master.zip
RUN rm master.zip
WORKDIR  /wtdbg2-master/
RUN make
ENV PATH /wtdbg2-master/:$PATH
