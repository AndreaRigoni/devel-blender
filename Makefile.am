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


## ////////////////////////////////////////////////////////////////////////////////
## //  QWS  ///////////////////////////////////////////////////////////////////////
## ////////////////////////////////////////////////////////////////////////////////
#
# QWS are the qtcreator work spaces files.. they needs to be compiled with the
# absolute path so then a template is filled using the path discovered by
# autotools to create the correct project paths in qtcreator for "edit" target

## PERL SUBST ##
__ax_pl_envsubst = $(PERL) -pe 's/([^\\]|^)\$$\{([a-zA-Z_][a-zA-Z_0-9]*)\}/$$1.$$ENV{$$2}/eg' < $1 > $2

SUFFIXES = .qws .qws.template

.qws.template.qws:
	@ $(call __ax_pl_envsubst,$<,$@);

export top_srcdir
export top_builddir
export abs_top_srcdir
export abs_top_builddir

QWS_FILES = $(top_builddir)/conf/ide/qtcreator/QtProject/qtcreator/devel-blender.qws
CLEANFILES = $(QWS_FILES)
qws: $(QWS_FILES)
edit_DEPS = qws
