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



dnl Process this file with autoconf to produce a configure script.

dnl AUTOCONF ///////////////////////////////////////////////////////////////////
AC_PREREQ([2.69])
AC_INIT([devel-blender], [0.1], [andrea.rgn@gmail.com])
AC_CONFIG_MACRO_DIRS([conf/m4])
AC_CONFIG_AUX_DIR([conf])
dnl AC_CONFIG_SRCDIR([...])
AC_CANONICAL_TARGET

dnl AUTOMAKE ///////////////////////////////////////////////////////////////////
AM_INIT_AUTOMAKE([foreign subdir-objects])


dnl update submodules at first ... (must be cleaned out)
AS_IF([${srcdir}/conf/update_submodules.sh],
      [AS_ECHO(["Submodules succesfully updated"])],
      [AS_ECHO(["Error updating submodules"])])


dnl AX_KCONFIG /////////////////////////////////////////////////////////////////
dnl see: m4/ax_enable_kconfig.m4
AS_VAR_SET([srcdir],[${srcdir}])
AS_VAR_SET([builddir],[$(pwd)])
# AS_VAR_SET([DOCKER_IMAGE],[consorziorfx/devel-blender:0.1])

AX_KCONFIG([conf/kconfig])

dnl AX_TARGET_SELFHELP /////////////////////////////////////////////////////////
AX_TARGET_SELFHELP

# //////////////////////////////////////////////////////////////////////////// #
# //  DOCKER BUILD /////////////////////////////////////////////////////////// #
# //////////////////////////////////////////////////////////////////////////// #

m4_sinclude(conf/kscripts/docker.ac)
AX_DOCKER_BUILD

# //////////////////////////////////////////////////////////////////////////// #

AC_CONFIG_HEADERS([config.h])

dnl RELEASE
AX_IS_RELEASE([always])
AK_ENABLE_DEBUG([no],,,,[-O3])
AC_SUBST([ENABLE_DEBUG],[${ax_enable_debug}])

# Checks for programs.
AC_PROG_AWK
AC_PROG_MKDIR_P
AC_PROG_LN_S
AC_PROG_SED
AC_PROG_CC
AC_PROG_CXX

AC_CHECK_PROGS([CURL],[curl])
AC_CHECK_PROGS([TAR],[gtar tar])
AC_CHECK_PROGS([UNIQ],[uniq])
AC_CHECK_PROGS([WC],[wc])

AC_PROG_LEX([noyywrap])
AC_PROG_YACC


# needed for sh_envsubst
AC_CHECK_PROGS([PERL],[perl])

## LIBTOOL
## LT_INIT()

## /////////////////////////////////////////////////////////////////////////////
## //  KSCRIPTS  ///////////////////////////////////////////////////////////////
## /////////////////////////////////////////////////////////////////////////////

## BUILD_COMMON ##
m4_sinclude(conf/kscripts/build_common.ac)

## TOOLCHAIN ##
# m4_sinclude(conf/kscripts/toolchain.ac)

## CODAC ##
# m4_sinclude(conf/kscripts/iter_codac.ac)

## QT ##
# m4_sinclude(conf/kscripts/qtdesktop.ac)

## NODEJS ##
# m4_sinclude(conf/kscripts/nodejs.ac)

## DOXYGEN ##
# m4_sinclude(conf/autoconf-doxygen/doxygen.ac)

## EXT_LIBJIT ##
# m4_sinclude(conf/kscripts/ext_libjit.ac)

## EXT_LLVM ##
# m4_sinclude(conf/kscripts/ext_llvm.ac)

## EXT_CCSTICKERS ##
# m4_sinclude(conf/kscripts/ext_ccStickers.ac)

## EXT_NODEJS_NODE ##
# m4_sinclude(conf/kscripts/ext_nodejs_node.ac)

## EXT_MDSPLUS ##
# m4_sinclude(conf/kscripts/ext_mdsplus.ac)


## BLENDER BUILD ##
AX_KCONFIG_VAR_WITH([BLENDER_BUILD_URL],["set blender url"])
AC_SUBST([BLENDER_BUILD_URL])
AX_KCONFIG_VAR_WITH([BLENDER_BUILD_BRANCH],["set blender branch"])
AC_SUBST([BLENDER_BUILD_BRANCH])

## // GIT IGNORE // ##
AX_GITIGNORE_ADD_PATH([${builddir}])
AX_GITIGNORE_ADD_PATH([${builddir}/src/build*])
AX_GITIGNORE_SUBST


AC_CONFIG_FILES( 
                 Makefile
				 .gitignore
				 docker/Makefile
				 ext/Makefile
				src/Makefile
               )
AC_OUTPUT
