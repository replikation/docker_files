FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y git wget cpanminus build-essential python r-base
RUN apt-get clean

ARG UNAME=opera
ARG UID=1000
ARG GID=1000
RUN groupadd -g $GID -o $UNAME
RUN useradd -m -u $UID -g $GID -o -s /bin/bash $UNAME
USER $UNAME

WORKDIR /home/$UNAME/
RUN git clone https://github.com/CSB5/OPERA-MS.git operams

WORKDIR /home/$UNAME/operams
USER root
RUN make
# These are dropbox links, so check the github if something breaks here
RUN wget --no-check-certificate -O /home/opera/operams/genomeDB_Sketch.msh \
https://www.dropbox.com/s/kot086vh26nds6j/genomeDB_Sketch.msh?dl=0
RUN wget --no-check-certificate -O /home/opera/operams/complete_ref_genomes.tar.gz \
https://www.dropbox.com/s/wcxvy2u0yhp3pw0/complete_ref_genomes.tar.gz?dl=0

RUN tar -xvzf /home/opera/operams/complete_ref_genomes.tar.gz && touch /home/opera/operams/database_updated

USER $UNAME
ENTRYPOINT ["perl", "OPERA-MS.pl"]
