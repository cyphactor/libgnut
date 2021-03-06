# Must contain a call to AC_INIT before the checks, and call to
# AC_OUTPUT at the end.
#
# The layout of standard autoconf.ac
#
# AC_INIT(package, version, bug-report-address)
# information on the package
# checks for programs
# checks for libraries
# checks for header files
# checks for types
# checks for structures
# checks for compiler characteristics
# checks for library functions
# checks for system services
# AC_CONFIG_FILES([file...])
# AC_OUTPUT
#

AC_PREREQ(2.59)
AC_INIT(Gnutella Library, 0.1.0, cyphactor@gmail.com, lib_gnut)
AM_INIT_AUTOMAKE
AC_CONFIG_SRCDIR([src/gnut_msgs.c])
AM_CONFIG_HEADER([src/config.h])

# checks for programs
AC_LIBTOOL_WIN32_DLL
AC_PROG_LIBTOOL
AC_PROG_CC

# checks for libraries

case $host in
    *mingw32*) GNUT_SYSTEM='-Wl,--output-def,.libs/libgnut.def,-s -L../lib -lsxs-0' ;;
    *-apple-darwin*) GNUT_SYSTEM='-Wl,-prebind,-seg1addr,0xC0000000 -lsxs' ;;
    *) GNUT_SYSTEM='-lsxs' ;;
esac

case $host in
    *mingw32*) GNUT_CFLAGS='-I../include' ;;
    *) GNUT_CFLAGS='' ;;
esac

AC_SUBST([GNUT_SYSTEM])
AC_SUBST([GNUT_CFLAGS])

# checks for header files
AC_HEADER_STDC
#AC_CHECK_HEADERS([arpa/inet.h netinet/in.h string.h sys/socket.h stdint.h])

# checks for types

# checks for structures

# checks for compiler characteristics
AC_C_BIGENDIAN(
[AH_VERBATIM([WORD_BIGENDIAN],
[
/* This a custom Verbatim macro template created to handle proper compiler based big-endian detection on apple machines when building universal binaries. This is needed because autoconf normally will only check the endianness of the system it is running on, not the system that the other systems that are cross-compiled for when building universal binaries. */
#ifdef __APPLE__
#ifdef __BIG_ENDIAN__
#define WORD_BIGENDIAN 1
#endif
#else
#define WORD_BIGENDIAN 1
#endif])],
[AH_VERBATIM([WORD_BIGENDIAN],[
/* This a custom Verbatim macro template created to handle proper compiler based big-endian detection on apple machines when building universal binaries. This is needed because autoconf normally will only check the endianness of the system it is running on, not the system that the other systems that are cross-compiled for when building universal binaries. */
#ifdef __APPLE__
#ifdef __BIG_ENDIAN__
#define WORD_BIGENDIAN 1
#endif
#endif])],
[AH_VERBATIM([WORD_BIGENDIAN],[
/* This a custom Verbatim macro template created to handle proper compiler based big-endian detection on apple machines when building universal binaries. This is needed because autoconf normally will only check the endianness of the system it is running on, not the system that the other systems that are cross-compiled for when building universal binaries. */
#ifdef __APPLE__
#ifdef __BIG_ENDIAN__
#define WORD_BIGENDIAN 1
#endif
#endif])])

# checks for library functions
#AC_CHECK_FUNCS([memset socket])

# checks for system services

AC_CONFIG_FILES([Makefile src/Makefile])
AC_OUTPUT
