FROM ubuntu:13.10
MAINTAINER Tobias Raeder tobias.raeder@gmail.com

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ saucy main\n" >> /etc/apt/sources.list
RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ saucy-updates main\n" >> /etc/apt/sources.list
RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ saucy universe\n" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y git
RUN apt-get install -y build-essential
RUN apt-get build-dep -y rxvt-unicode
RUN apt-get install -y wget

WORKDIR /tmp
RUN wget http://dist.schmorp.de/rxvt-unicode/rxvt-unicode-9.19.tar.bz2
RUN tar xjf rxvt-unicode-9.19.tar.bz2
RUN mkdir -p /opt
RUN mv /tmp/rxvt-unicode-9.19 /opt/rxvt-unicode
WORKDIR /opt/rxvt-unicode

RUN /opt/rxvt-unicode/configure --prefix=/usr/local/stow/rxvt-unicode --enable-256-color --enable-unicode3
RUN make
RUN make install

CMD /bin/bash
