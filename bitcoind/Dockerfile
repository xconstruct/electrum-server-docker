FROM ubuntu:14.04
MAINTAINER Antonin Hildebrand <antonin@binaryage.com>

RUN apt-get update
RUN apt-get install -y wget bsdmainutils make g++ python-leveldb libboost-all-dev libssl-dev libdb++-dev pkg-config
RUN wget https://bitcoin.org/bin/0.9.2/bitcoin-0.9.2-linux.tar.gz
RUN sha256sum bitcoin-0.9.2-linux.tar.gz | grep 58a77aeb4c81b54d3903d85abce4f0fb580694a3611a415c5fe69a27dea5935b
RUN tar xfz bitcoin-0.9.2-linux.tar.gz
RUN cd bitcoin-0.9.2-linux/src && tar xfz bitcoin-0.9.2.tar.gz
RUN cd bitcoin-0.9.2-linux/src/bitcoin-0.9.2 && ./configure --disable-wallet --without-miniupnpc
RUN cd bitcoin-0.9.2-linux/src/bitcoin-0.9.2 && make
RUN strip bitcoin-0.9.2-linux/src/bitcoin-0.9.2/src/bitcoind
RUN cp -a bitcoin-0.9.2-linux/src/bitcoin-0.9.2/src/bitcoind /bin/bitcoind

ADD . /bitcoind
WORKDIR /bitcoind

EXPOSE 8333
EXPOSE 8332

ADD	enter /enter
RUN	chmod +x /enter
ENTRYPOINT ["/enter"]
