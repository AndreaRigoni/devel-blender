FROM ubuntu:18.04

## DEVEL BASE ##

RUN apt-get -y update && apt-get -y install build-essential \
    gawk \
    git \
    autoconf \
    automake \
    libtool \
	locales
#
# NOTE: gawk is needed for docker build to match gawk in system...
#

RUN apt-get -y update && apt-get -y install tmux \
	wget zip vim emacs

## QT ##
RUN apt-get -y update && apt-get -y install qtbase5-dev \
											libxcb-xinerama0-dev \
											python

RUN apt-get -y update && apt-get -y install qtcreator


# BLENDER NEEDS #
RUN apt-get -y update && apt-get -y install cmake cmake-gui sudo figlet
COPY install_blender_deps.sh /
RUN /install_blender_deps.sh --no-confirm --build-oiio --skip-llvm
