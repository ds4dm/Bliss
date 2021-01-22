dnl Process this file with autoconf to produce a configure script.
AC_PREREQ([2.69])
LT_PREREQ([2.4.2])
dnl
AC_INIT([bliss],[0.73+debian-1+sage-2016-08-02],
	[tommi.junttila@aalto.fi],[bliss],
	[http://www.tcs.hut.fi/Software/bliss/])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_SRCDIR([bliss_C.h])
AC_CONFIG_HEADERS([bliss_config.h])
AM_SILENT_RULES([yes])
AM_INIT_AUTOMAKE([foreign])
AM_MAINTAINER_MODE([])

AC_CANONICAL_HOST

dnl libtool
LT_INIT

dnl Checks for programs:
AC_PROG_CXX
AC_PROG_CC

AC_ARG_ENABLE([gmp],
  [AS_HELP_STRING([--enable-gmp@<:@=ARG@:>@],
      [enable use of GMP @<:@default=yes@:>@])],
  [:],
  [enable_gmp=yes])
AS_IF([test "x$enable_gmp" = xyes],
  [
   dnl Checks for libraries:
   dnl GNU MultiPrecision arithmetic library (GMP)
   AM_PATH_GMP([5.1.3],[],[AC_MSG_ERROR(could not find required version of GMP)])
  ])
AM_CONDITIONAL(GMP, test "x$enable_gmp" = xyes)

AC_CONFIG_FILES([
	include/Makefile
	include/bliss/Makefile
	Makefile
	])
AC_OUTPUT

dnl eof

