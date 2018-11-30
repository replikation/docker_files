FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN apt-get update && apt-get install -y python3-setuptools \
					 virtualenv \
					 libncurses5-dev \
					 python3-dev
# Install pip
RUN curl https://bootstrap.pypa.io/get-pip.py -o /root/get-pip.py
RUN python3 /root/get-pip.py
RUN pip3 install --upgrade pip

# wget latest release
RUN DWNL=$(curl -s https://github.com/nanoporetech/medaka/releases | grep "tar.gz" | head -1 | cut -f2 -d'"') && wget https://github.com/${DWNL}
RUN /bin/bash -c "tar -xf *tar.gz"
RUN /bin/bash -c "rm -f *tar.gz"
RUN mv medaka* medaka/
WORKDIR medaka
RUN make install
ENV PATH=/medaka/venv/bin/:$PATH
