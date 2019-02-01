FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
# install samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2
RUN tar xjf samtools*.tar.bz2 && rm samtools*.tar.bz2
RUN mv /samtools-*/ /samtools/
WORKDIR  /samtools/
RUN ./configure --without-curses
RUN make
RUN make install
# wtdbg2
WORKDIR /
RUN git clone https://github.com/ruanjue/wtdbg2.git
RUN cd wtdbg2/ && make
ENV PATH /wtdbg2/:$PATH
# minimap2
RUN git clone https://github.com/lh3/minimap2
RUN cd minimap2 && make
ENV PATH /minimap2/:$PATH
