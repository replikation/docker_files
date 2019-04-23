FROM ubuntu:xenial
MAINTAINER Christian Brandt <christian.jena@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get upgrade
RUN	apt-get install -y \
			libatlas-base-dev \
			libbz2-dev \
			libffi-dev \
			libhdf5-dev \
			liblzma-dev \
			libncurses5-dev \
			libopenblas-base \
			libopenblas-dev \
			zlib1g-dev \
			make \
			python3-all-dev \
			virtualenv \
			wget \
			bzip2 \
			cmake \
			gcc-4.9 \
			git \
			g++-4.9

RUN apt-get clean all && \
		apt-get purge && \
		rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV CXX="g++-4.9" CC="gcc-4.9"

RUN mkdir /ONT && \
	cd /ONT && \
	git clone --recursive https://github.com/nanoporetech/pomoxis && \
	cd pomoxis && \
	make install

# Create a activating environment after a docker run
# from dpirdmk/pomoxis
RUN echo "#!/bin/bash" > /usr/local/bin/init.sh && \
		echo ". /ONT/pomoxis/venv/bin/activate" >> /usr/local/bin/init.sh && \
    echo "exec \"\$@\"" >> /usr/local/bin/init.sh && \
    chmod +x /usr/local/bin/init.sh && \
    ln -s /usr/local/bin/init.sh /

ENTRYPOINT ["init.sh"]
CMD ["/bin/bash"]
