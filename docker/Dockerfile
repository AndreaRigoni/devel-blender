FROM ubuntu:18.04


RUN apt-get -y update && apt-get install -y build-essential \
                       git \
					   autoconf \
					   automake \
					   autoheader \
					   libtool

RUN apt-get -y update && apt-get -y install qtbase5-dev \
	                                        libxcb-xinerama0-dev \
											python

RUN apt-get -y update && apt-get -y install tmux \
	wget \
	zip \
	git \
	vim
