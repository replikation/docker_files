FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN wget https://github.com/ruanjue/wtdbg2/archive/master.zip
RUN unzip master.zip
RUN cd wtdbg2 && make
ENV PATH /wtdbg2/:$PATH
