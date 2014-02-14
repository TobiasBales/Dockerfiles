FROM ubuntu:13.10
MAINTAINER Tobias Raeder tobias.raeder@gmail.com

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -y build-essential
RUN apt-get install -y libssl-dev
RUN apt-get install -y zlib1g-dev
RUN apt-get install -y e2fslibs-dev
RUN apt-get install -y curl

RUN curl https://www.tarsnap.com/download/tarsnap-autoconf-1.0.35.tgz > /tmp/tarsnap.tar.gz
RUN tar xzf /tmp/tarsnap.tar.gz -C /
WORKDIR /tarsnap-autoconf-1.0.35

RUN ./configure --prefix=/usr/local/stow/tarsnap
RUN make
RUN make install

CMD /bin/bash
