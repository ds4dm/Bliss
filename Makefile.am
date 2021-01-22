ACLOCAL_AMFLAGS = -I m4

AUTOMAKE_OPTIONS = \
	dist-xz \
	dist-bzip2 \
	dist-zip

AM_DISTCHECK_CONFIGURE_FLAGS ?= \
	--disable-maintainer-mode \
	--enable-extended-tests

## Library versioning (C:R:A == current:revision:age)
## 0.73 2:0:0
LIBBLISS_LT_VERSION = 2:0:0

SUBDIRS = include .

AM_CFLAGS = -g -pedantic -Wall -O3

pkginclude_HEADERS = \
	bignum.hh \
	kqueue.hh \
	kstack.hh \
	defs.hh \
	graph.hh \
	partition.hh \
	orbit.hh \
	uintseqhash.hh \
	heap.hh \
	timer.hh \
	utils.hh \
	bliss_C.h

lib_LTLIBRARIES = libbliss.la

bin_PROGRAMS = bliss

libbliss_la_SOURCES = \
	defs.cc \
	graph.cc \
	partition.cc \
	orbit.cc \
	uintseqhash.cc \
	heap.cc \
	timer.cc \
	utils.cc \
	bliss_C.cc

libbliss_la_CXXFLAGS = \
	-I $(top_builddir)/include

if GMP
libbliss_la_CXXFLAGS += \
	-D BLISS_USE_GMP \
	$(GMP_CFLAGS)
endif

libbliss_la_CFLAGS = \
	$(libbliss_la_CXXFLAGS)

libbliss_la_LDFLAGS = \
	-version-info $(LIBBLISS_LT_VERSION)

libbliss_la_LIBADD = \
	$(GMP_LIBS)

bliss_SOURCES = \
	bliss.cc

bliss_CXXFLAGS = \
	$(libbliss_la_CXXFLAGS)

bliss_LDADD = \
	$(top_builddir)/libbliss.la \
	$(GMP_LIBS)
