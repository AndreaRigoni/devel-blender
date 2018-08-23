include $(top_srcdir)/Common.mk

SUBDIRS =

if ENABLE_NODEJS
SUBDIRS += nodejs
endif

if ENABLE_QT
SUBDIRS += qt_example
endif

bin_PROGRAMS = main
main_SOURCES = main.cpp


## ////////////////////////////////////////////////////////////////////////////////
## //  BLENDER  ///////////////////////////////////////////////////////////////////
## ////////////////////////////////////////////////////////////////////////////////

DOWNLOADS += blender

blender: ##@ext download blender
blender_URL    ?= https://git.blender.org/blender.git
blender_BRANCH  = blender2.8


build-deps: USER=root
build-deps:
	@ $(FIGLET) "build deps"; \
	  . blender/build_files/build_environment/install_deps.sh --no-build --no-confirm


init: ##@blender initialize repository
init: | blender build-deps

build: ##@blender build blender
build: | blender
	@ $(FIGLET) "build blender"; \
	  $(MAKE) -C blender debug

run: ##@blender run blender
run:
	@ $(FIGLET) "run blender"; \
	  ./build_linux_debug/bin/blender
