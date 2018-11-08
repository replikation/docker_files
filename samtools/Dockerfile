FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN apt-get update
RUN apt-get clean
RUN wget https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2
RUN tar xjf samtools*.tar.bz2 ; rm samtools*.tar.bz2
WORKDIR  /samtools-*/
RUN ./configure --without-curses
RUN make
RUN make install
