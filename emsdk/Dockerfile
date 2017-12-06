From ubuntu:16.04
SHELL ["/bin/bash", "-c"]

RUN sed -i".bak" -e 's/\/\/archive.ubuntu.com/\/\/ftp.jaist.ac.jp\/pub\/Linux/g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
# cmake \
                gcc \
                git \
                python2.7 \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*
RUN ln -s /usr/bin/python2.7 /usr/bin/python

RUN git clone https://github.com/juj/emsdk.git
WORKDIR /emsdk
RUN ./emsdk install latest
RUN ./emsdk activate latest
# RUN bash -l -c "source /emsdk/emsdk_env.sh --build=Release"
RUN echo "source /emsdk/emsdk_env.sh --build=Release" > /root/.bash_profile

# Clean up extra dependencies
RUN apt-get purge -y git && apt-get -y autoremove

COPY ./src /src
WORKDIR /src

