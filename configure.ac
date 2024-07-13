AC_INIT([enigma2-plugins],[4],[forum@openpli.org])
AM_INIT_AUTOMAKE([dist-bzip2 foreign no-define tar-pax])
AC_CONFIG_HEADERS([enigma2-plugins-config.h])

# Silent rules are available since 1.11, but older versions
# are still in use. So don't use them unconditionally.
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

AC_USE_SYSTEM_EXTENSIONS
AC_SYS_LARGEFILE

AC_PROG_CC
AC_PROG_CXX
m4_ifdef([LT_INIT], [LT_INIT], [AC_PROG_LIBTOOL])
AC_CONFIG_MACRO_DIR([m4])

AC_PATH_PROG(MSGFMT, msgfmt, AC_MSG_ERROR(Could not find msgfmt))

AM_PATH_PYTHON
AX_PYTHON_DEVEL
AX_PTHREAD

TUXBOX_APPS_DVB


AC_ARG_WITH(debug,
	AS_HELP_STRING([--without-debug],[disable debugging code]),
	[with_debug="$withval"],[with_debug="yes"])
if test "$with_debug" = "yes"; then
	DEBUG_CFLAGS="-ggdb3"
	AC_DEFINE([DEBUG],[1],[Define to 1 to enable debugging code])
fi
AC_SUBST(DEBUG_CFLAGS)

AC_ARG_WITH(po,
	AS_HELP_STRING([--with-po],[enable updating of po files]),
	[with_po="$withval"],[with_po="no"])
if test "$with_po" = "yes"; then
	AC_PATH_PROG(MSGINIT, msginit)
	AC_PATH_PROG(MSGMERGE, msgmerge)
	AC_PATH_PROG(MSGUNIQ, msguniq)
	AC_PATH_PROG(MSGATTRIB, msgattrib)
	AC_PATH_PROG(XGETTEXT, xgettext)
	if test -z "$MSGINIT" -o -z "$MSGMERGE" -o -z "$MSGUNIQ" -o -z "$MSGATTRIB" -o -z "$XGETTEXT"; then
		AC_MSG_ERROR([Could not find required gettext tools])
	fi
fi
AM_CONDITIONAL(UPDATE_PO, test "$with_po" = "yes")

AC_CONFIG_FILES([
Makefile

lcd4linux/Makefile
lcd4linux/src/Makefile
lcd4linux/src/data/Makefile
lcd4linux/src/data/audio/Makefile
lcd4linux/src/data/Clock1/Makefile
lcd4linux/src/data/Clock2/Makefile
lcd4linux/src/data/Clock3/Makefile
lcd4linux/src/data/Clock4/Makefile
lcd4linux/src/data/Clock5/Makefile
lcd4linux/src/data/Clock6/Makefile
lcd4linux/src/data/Clock7/Makefile
lcd4linux/src/data/Clock8/Makefile
lcd4linux/src/data/Clock9/Makefile
lcd4linux/src/data/Clock10/Makefile
lcd4linux/src/meteo/Makefile
lcd4linux/src/wetter/Makefile
lcd4linux/src/renderer/Makefile
lcd4linux/po/Makefile
lcd4linux/meta/Makefile

moviecut/Makefile
moviecut/meta/Makefile
moviecut/src_cc/Makefile
moviecut/src_py/Makefile
moviecut/po/Makefile

networkbrowser/Makefile
networkbrowser/meta/Makefile
networkbrowser/po/Makefile
networkbrowser/src/Makefile
networkbrowser/src/icons/Makefile
networkbrowser/src/lib/Makefile

vps/Makefile
vps/meta/Makefile
vps/po/Makefile
vps/src_cc/Makefile
vps/src_py/Makefile

])
AC_OUTPUT
