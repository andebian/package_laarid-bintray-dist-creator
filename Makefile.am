ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}

# Distribution
# ------------
EXTRA_DIST = \
	LICENSE \
	README.md
BUILT_SOURCES =
CLEANFILES =
DISTCLEANFILES = \
	config.lt
MAINTAINERCLEANFILES = \
	$(GITIGNORE_MAINTAINERCLEANFILES_TOPLEVEL) \
	$(GITIGNORE_MAINTAINERCLEANFILES_M4_LIBTOOL) \
	$(GITIGNORE_MAINTAINERCLEANFILES_MAKEFILE_IN)

# We're running CI in docker, which reports host architecture as host,
# not the docker image architecture as we expected, so specifying the
# host/build information is necessary here.
DISTCHECK_CONFIGURE_FLAGS = \
	--host=$(host_alias) \
	--build=$(build_alias) \
	--disable-maintainer-mode

GITIGNOREFILES = \
	build \
	debian \
	$(DIST_ARCHIVES)

# Common/global flags
# -------------------
AM_CPPFLAGS = \
	-include config.h \
	-Iinclude \
	-I$(top_srcdir)/include

AM_CFLAGS = \
	-Wall -Werror \
	-std=gnu99

AM_CXXFLAGS = \
	-Wall -Werror \
	-std=gnu++11

libtool_opts = \
	-version-info $(LT_VERSION_INFO) \
	-export-dynamic \
	-rpath $(libdir)

lib_LTLIBRARIES = \
	libandroid-dummy.la

# libandroid-dummy.la
# ------------
libandroid_dummy_la_LDFLAGS = \
	$(libtool_opts)
libandroid_dummy_la_SOURCES = \
	src/dummy.c

# dummy HEADERS
# --------------
dummyincdir = $(includedir)/android/dummy-$(DUMMY_API_VERSION)/laarid
dummyinc_HEADERS = \
	include/laarid/dummy.h

CLEANFILES += $(BUILT_SOURCES)
GITIGNOREFILES += $(BUILT_SOURCES)

-include $(top_srcdir)/git.mk
