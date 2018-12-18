FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>

RUN apt-get update \
  && apt-get install -y \
  ncbi-blast+ \
  default-jre \
  python3-dev \
  python3-pip \
  cmake \
  && apt-get clean
RUN mkdir unicycler
WORKDIR unicycler

# Install SPAdes
RUN wget "http://cab.spbu.ru/files/release3.11.1/SPAdes-3.11.1.tar.gz"
RUN tar -xzf SPAdes-3.11.1.tar.gz
RUN mkdir -p /unicycler/SPAdes-3.11.1-Linux/src/build
WORKDIR /unicycler/SPAdes-3.11.1/src/build
RUN cmake ..
RUN make install
WORKDIR /unicycler
RUN rm -r SPAdes-3.11.1-Linux*

# Install racon
RUN git clone --recursive https://github.com/isovic/racon.git racon
RUN mkdir -p /unicycler/racon/build

WORKDIR /unicycler/
RUN wget https://github.com/Kitware/CMake/releases/download/v3.13.2/cmake-3.13.2.tar.gz
RUN sh -c 'tar -xzf cmake-*.tar.gz'
WORKDIR /unicycler/cmake-3.13.2/
RUN ./configure
RUN make && make install
RUN rm -r /unicycler/cmake*

WORKDIR /unicycler/racon/build
RUN cmake -DCMAKE_BUILD_TYPE=Release ..
RUN make && make install
WORKDIR /unicycler/
RUN rm -r racon*

# Install samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2
RUN tar xjf samtools*.tar.bz2 ; rm samtools*.tar.bz2
RUN mv /unicycler/samtools-*/ /unicycler/samtools/
WORKDIR  /unicycler/samtools/
RUN ./configure --without-curses
RUN make && make install
WORKDIR /unicycler
RUN rm -r samtools*

# Install bowtie2
RUN wget https://github.com/BenLangmead/bowtie2/releases/download/v2.3.4.3/bowtie2-2.3.4.3-linux-x86_64.zip
RUN unzip bowtie2-*.zip
RUN mv /unicycler/bowtie2-*/ /unicycler/bowtie2/
WORKDIR /unicycler/bowtie2/
RUN mv bowtie2* /usr/local/bin
WORKDIR /unicycler
RUN rm -r bowtie2*

# Install Pilon
WORKDIR /usr/local/bin/
RUN wget "https://github.com/broadinstitute/pilon/releases/download/v1.22/pilon-1.22.jar"

# Install Unicycler
WORKDIR /unicycler
RUN git clone https://github.com/rrwick/Unicycler.git
WORKDIR /unicycler/Unicycler
ENV TERM=xterm
RUN python3 setup.py install
WORKDIR /unicycler
RUN rm -r Unicycler

# ENTRYPOINT
ENTRYPOINT ["unicycler"]
CMD ["--help"]
