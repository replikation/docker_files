FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN apt-get update
RUN apt-get install -y python-dev python-tk
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py
RUN pip install numpy
RUN pip install scipy
RUN pip install matplotlib
RUN sed -i 's/tkagg/agg/g' /usr/local/lib/python2.7/dist-packages/matplotlib/mpl-data/matplotlibrc
RUN /bin/sh -c "echo 'backend: Agg' > ~/.config/matplotlib/matplotlibrc"
RUN pip install sourmash
