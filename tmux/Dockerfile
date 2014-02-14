FROM ubuntu:13.10
MAINTAINER Tobias Raeder tobias.raeder@gmail.com

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ saucy main\n\n" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y automake
RUN apt-get install -y autoconf
RUN apt-get install -y libtool
RUN apt-get install -y pkg-config
RUN apt-get install -y git
RUN apt-get build-dep -y tmux

RUN mkdir -p /opt/tmux
WORKDIR /opt/tmux

RUN git pull --rebase || git clone git://git.code.sf.net/p/tmux/tmux-code /opt/tmux
RUN /opt/tmux/autogen.sh
RUN /opt/tmux/configure --prefix=/usr/local/stow/tmux
RUN make
RUN make install

CMD /bin/bash
