# versioning
# ----------
# To make new release:
#
#   dummy_micro_version += 1
#   dummy_interface_revision += 1
#
# if any functions have been added:
#
#   dummy_micro_version += 1
#   dummy_interface_revision = 0
#
#   or
#
#   dummy_minor_version += 1
#   dummy_micro_version = 0
#   dummy_interface_revision = 0
#
# if backwards compatibility has been broken:
#
#   dummy_major_version += 1
#   dummy_minor_version = 0
#   dummy_micro_version = 0
#   dummy_interface_revision = 0
m4_define([dummy_major_version], [0])
m4_define([dummy_minor_version], [0])
m4_define([dummy_micro_version], [1])
m4_define([dummy_interface_revision], [1])
m4_define([dummy_api_version], [dummy_major_version.0])
m4_define([dummy_release_number], [dummy_major_version])
m4_define([dummy_version],
  [dummy_major_version.dummy_minor_version.dummy_micro_version])

AC_INIT([dummy], [dummy_version],
  [https://github.com/vicamo/bintray-dist-creator/issues], [],
  [https://github.com/vicamo/bintray-dist-creator])

AC_CONFIG_HEADERS([config.h])
AC_CONFIG_SRCDIR([include/dummy/dummy.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])

AM_INIT_AUTOMAKE([-Wall -Werror foreign subdir-objects no-define tar-ustar])
AM_MAINTAINER_MODE([enable])
AM_SILENT_RULES([yes])

DUMMY_MAJOR_VERSION=dummy_major_version
DUMMY_MINOR_VERSION=dummy_minor_version
DUMMY_MICRO_VERSION=dummy_micro_version
DUMMY_API_VERSION=dummy_api_version
DUMMY_RELEASE_NUMBER=dummy_release_number
AC_SUBST([DUMMY_MAJOR_VERSION])
AC_SUBST([DUMMY_MINOR_VERSION])
AC_SUBST([DUMMY_MICRO_VERSION])
AC_SUBST([DUMMY_API_VERSION])
AC_SUBST([DUMMY_RELEASE_NUMBER])

# Define _GNU_SOURCE etc. where appropriate, e.g. for strptime() on glibc
AC_USE_SYSTEM_EXTENSIONS

AM_PROG_AR
AC_PROG_CC

# libtool versioning
# ------------------
LT_INIT

m4_define([dummy_binary_age], [m4_eval(100 * dummy_minor_version + dummy_micro_version)])
m4_define([lt_current], [m4_eval(dummy_binary_age - dummy_interface_revision)])
m4_define([lt_revision], [dummy_interface_revision])
# Whenever backward compatibility is broken, we generate libraries of different
# release number. That follows the library files of the same release are always
# compatible, and they have their lt_age equal to lt_current.
m4_define([lt_age], [lt_current])
LT_VERSION_INFO="lt_current:lt_revision:lt_age"
AC_SUBST([LT_VERSION_INFO])

LT_OUTPUT

AC_LANG_C

AC_CONFIG_FILES([
  Makefile
])
AC_OUTPUT
