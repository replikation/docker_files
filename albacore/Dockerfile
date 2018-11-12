FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN wget https://mirror.oxfordnanoportal.com/software/analysis/ont_albacore-2.3.3-cp34-cp34m-manylinux1_x86_64.whl
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python3 get-pip.py
RUN pip install ont_albacore-*-cp34-cp34m-manylinux1_x86_64.whl
