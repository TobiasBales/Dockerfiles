FROM ubuntu
MAINTAINER Tobias Raeder tobias.raeder@gmail.com

RUN echo "deb-src http://archive.ubuntu.com/ubuntu/ precise main\n\n" >> /etc/apt/sources.list
#RUN echo "deb http://archive.ubuntu.com/ubuntu/ precise universe\n" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y git
RUN apt-get build-dep -y emacs

#RUN git clone git://git.savannah.gnu.org/emacs.git /opt/emacs
RUN git clone git://repo.or.cz/emacs.git /opt/emacs
#RUN /opt/vim/configure --prefix=/usr/local/stow/vim --enable-gui=no --without-x --disable-nls --enable-multibyte --with-tlib=ncurses --enable-pythoninterp --enable-rubyinterp --with-features=huge
WORKDIR /opt/emacs

RUN /opt/emacs/autogen.sh
RUN /opt/emacs/configure --prefix=/usr/local/stow/emacs
RUN make
RUN make install

CMD /bin/bash
