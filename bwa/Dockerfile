FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
git clone https://github.com/lh3/bwa.git
WORKDIR  /bwa/
RUN make
ENV PATH /bwa/:$PATH
