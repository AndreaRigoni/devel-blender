include $(top_srcdir)/Common.mk
# include $(top_srcdir)/conf/kscripts/ext_ccStickers.mk
# include $(top_srcdir)/conf/kscripts/ext_mdsplus.mk

define _ext_bootstrap
$(eval
$1/configure: | $1
	@ cd $1; ./bootstrap
)
endef

define _ext_autogen_sh
$(eval
$1/configure: | $1
	@ cd $1; ./autogen.sh
)
endef

define _ext_configure
$(eval
$1/config.log: $1/configure
	@ cd $1; ./configure $($(subst -,_,$(subst ' ',_,$(subst .,_,$1)))_CONFIGURE_ARGS)
$1/Makefile: $1/config.log
	@ $(MAKE) $(AM_MAKEFLAGS) -C $1 Makefile
)
endef

ext-: ##@ext enter ext module with $TARGET
ext-%: %/Makefile
	@ $(MAKE) $(AM_MAKEFLAGS) -C $(subst ext-,,$@) $(TARGET)

all: TARGET = all
all: $(addprefix ext-,$(EXT_MODULES))

clean: TARGET = clean
clean: $(addprefix ext-,$(EXT_MODULES))


list: ##@ext list defined ext modules
list : _item = $(info | $1: ) $(foreach x,$($1),$(info |  - $x))
list:
	@ \
	$(info ,-----------------------------------------------------------------) \
	$(info | ext modules defined ) \
	$(info |) \
	$(call _item,EXT_MODULES) \
	$(info |) \
	$(info |) \
	$(info `-----------------------------------------------------------------) :

# /////////////////////////////////////////////////////////////////////////// //
# //  EXT MODULES  ////////////////////////////////////////////////////////// //
# /////////////////////////////////////////////////////////////////////////// //

DOWNLOADS  += $(EXT_MODULES)

ccStickers: ##@ext download ccStickers sources
ccStickers_URL = $(CCSTICKERS_URL)
$(call _ext_bootstrap,ccStickers)
$(call _ext_configure,ccStickers)

EXT_MDSPLUS_URL    ?= https://github.com/mdsplus/mdsplus.git
EXT_MDSPLUS_BRANCH ?= alpha
ext-mdsplus: AM_MAKEFLAGS += -j1
mdsplus: ##@ext mdsplus
mdsplus_URL    = $(EXT_MDSPLUS_URL)
mdsplus_BRANCH = $(EXT_MDSPLUS_BRANCH)
mdsplus_CONFIGURE_ARGS = $(EXT_MDSPLUS_CONFIGURE_ARGS)
$(call _ext_bootstrap,mdsplus)
$(call _ext_configure,mdsplus)





