include $(top_srcdir)/Common.mk

SUBDIRS =

bin_PROGRAMS = main
main_SOURCES = main.cpp


## ////////////////////////////////////////////////////////////////////////////////
## //  BLENDER  ///////////////////////////////////////////////////////////////////
## ////////////////////////////////////////////////////////////////////////////////

DOWNLOADS = blender

blender: ##@ext download blender
blender_URL    = $(BLENDER_BUILD_URL)
blender_BRANCH = $(BLENDER_BUILD_BRANCH)

build-deps: build_deps_CMD = blender/build_files/build_environment/install_deps.sh
build-deps: build_deps_ARG = --no-confirm --skip-llvm
build-deps: USER=root
build-deps:
	@ $(FIGLET) "build deps"; \
	  [ -e $(build_deps_CMD) ]  && $(build_deps_CMD) $(build_deps_ARG)

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

config: ##@blender configure build
config:
	  @ $(MAKE) -C blender $@

