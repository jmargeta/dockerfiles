FROM ubuntu:14.04
MAINTAINER Jan Margeta <jmargeta@gmail.com>

# Install dependencies
RUN apt-get update
RUN apt-get install automake git clang -y

# Get libccv
RUN mkdir -p /opt
RUN cd /opt && git clone https://github.com/liuliu/ccv.git

# Build the lib
RUN apt-get install build-essential wget -y
RUN cd /opt/ccv/lib && /opt/ccv/lib/configure && make

# Build the server
RUN apt-get install libev-dev -y
RUN apt-get install libdispatch-dev -y
RUN cd /opt/ccv/serve && make all

# run testing suite
RUN cd /opt/ccv/test && make all

WORKDIR /opt/ccv/serve/
ENTRYPOINT /opt/ccv/serve/ccv
