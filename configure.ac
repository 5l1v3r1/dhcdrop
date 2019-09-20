#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.61)
AC_INIT("DHCP-dropper", "0.5", "roma@ultranet.ru")
AC_CANONICAL_TARGET
AC_CONFIG_SRCDIR([src/dhcp.h])
AC_CONFIG_HEADER([config.h])

AM_INIT_AUTOMAKE(dhcdrop, "0.5")
AC_ARG_ENABLE([static-build],
	AC_HELP_STRING([--enable-static-build], [enable static build of program]),
	ENABLE_STATIC_BUILD=yes, [])
AM_CONDITIONAL([ENABLE_STATIC_BUILD], [test x$ENABLE_STATIC_BUILD = xyes])
# Checks for programs.
AC_LANG_C
AC_PROG_CC
AM_PROG_LIBTOOL

# Checks for libraries.
# FIXME: Replace `main' with a function in `-lpcap':
AC_CHECK_LIB([pcap], [main])

# Checks for header files.
AC_HEADER_STDC
AC_HEADER_SYS_WAIT
AC_CHECK_HEADERS([stdint.h stdio.h stdlib.h unistd.h errno.h string.h signal.h time.h arpa/inet.h \
					sys/wait.h sys/socket.h netinet/in.h], 
				[], [AC_MSG_ERROR([You need C devel package installed])])
AC_CHECK_HEADERS([pcap.h], [], [AC_MSG_ERROR([You need libpcap devel package installed])])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_C_INLINE
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_MALLOC
AC_FUNC_MEMCMP
AC_TYPE_SIGNAL
AC_CHECK_FUNCS([bzero inet_ntoa memset pcap_open_live pcap_inject pcap_datalink pcap_setnonblock \
				pcap_close pcap_compile pcap_setfilter pcap_freecode pcap_findalldevs pcap_freealldevs \
				pcap_perror pcap_dispatch ],
	[], [AC_MSG_ERROR([You need libpcap devel package installed])])

AC_CONFIG_FILES([Makefile src/Makefile man/Makefile man/ru/Makefile])
AC_OUTPUT
