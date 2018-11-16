FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN git clone --recursive https://github.com/jts/nanopolish
WORKDIR  /nanopolish/
RUN make
ENV PATH /nanopolish/:$PATH
ENV PATH /nanopolish/scripts/:$PATH

# make scripts executable & and add shebang
RUN sed -i '1i#!/usr/bin/env python3' /nanopolish/scripts/nanopolish_makerange.py
RUN chmod +x /nanopolish/scripts/nanopolish_makerange.py
RUN sed -i '1i#!/usr/bin/env python3' /nanopolish/scripts/nanopolish_merge.py
RUN chmod +x /nanopolish/scripts/nanopolish_merge.py

# install parallel
WORKDIR  /
RUN wget http://ftp.gnu.org/gnu/parallel/parallel-latest.tar.bz2
RUN tar xvjf parallel-latest.tar.bz2
RUN mv parallel-*/ parallel/
WORKDIR  /parallel/
RUN ./configure && make && make install
RUN rm -f parallel-latest.tar.bz2

# install bioclite
WORKDIR /
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python3 get-pip.py
RUN pip install biopython pysam
