FROM ubuntu:14.04
MAINTAINER Antonin Hildebrand <antonin@binaryage.com>

RUN apt-get update
RUN apt-get install -y g++ git python-dev python-setuptools python-openssl python-leveldb libleveldb-dev
RUN easy_install jsonrpclib plyvel

ADD	. /electrum
WORKDIR /electrum

RUN git clone https://github.com/spesmilo/electrum-server.git
WORKDIR /electrum/electrum-server
RUN chmod +x server.py

RUN ln -s /electrum/electrum-server/server.py /bin/electrum-server
RUN chmod +x /bin/electrum-server

EXPOSE 50001
EXPOSE 8081
EXPOSE 50002
EXPOSE 8082

ADD enter /enter
RUN	chmod +x /enter
ENTRYPOINT ["/enter"]
