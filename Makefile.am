## ////////////////////////////////////////////////////////////////////////// //
##
## This file is part of the autoconf-bootstrap project.
## Copyright 2018 Andrea Rigoni Garola <andrea.rigoni@igi.cnr.it>.
##
## This program is free software: you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation, either version 3 of the License, or
## (at your option) any later version.
##
## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License
## along with this program.  If not, see <http://www.gnu.org/licenses/>.
##
## ////////////////////////////////////////////////////////////////////////// //

include Common.mk

AM_MAKEFLAGS = -j$(MAKE_PROCESS)
ACLOCAL_AMFLAGS = -I conf/m4

SUBDIRS = ext src

all: ##@all all target
all: build

clean: ## clean

## ////////////////////////////////////////////////////////////////////////////////
## //  BLENDER  ///////////////////////////////////////////////////////////////////
## ////////////////////////////////////////////////////////////////////////////////
init:   ##@blender initialize repository
build:  ##@blender build blender
run:    ##@blender run blender
config: ##@blender configure cmake build (not working properely)
NODOCKERBUILD += init build run config
init build run config:
	@ $(MAKE) -C src $@



