FROM ubuntu:13.10
MAINTAINER Tobias Raeder tobias.raeder@gmail.com

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ saucy main\n\n" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y mercurial
RUN apt-get install -y libncurses5-dev
RUN apt-get build-dep -y vim

RUN mkdir -p /opt/vim
WORKDIR /opt/vim

RUN hg pull -u || hg clone https://vim.googlecode.com/hg/ /opt/vim
RUN /opt/vim/configure --prefix=/usr/local/stow/vim --disable-nls --enable-multibyte --with-tlib=ncurses --enable-pythoninterp --enable-rubyinterp --with-features=huge --with-gui --with-x
RUN make
RUN make install

CMD /bin/bash
