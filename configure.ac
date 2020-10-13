AC_PREREQ([2.57])
AC_INIT(xde-common,0.1, xinligg@gmail.com)
AM_INIT_AUTOMAKE([foreign])
dnl AC_PROG_INTLTOOL(, [no-xml])
dnl AM_MAINTAINER_MODE

# Checks for programs.
AC_PROG_INSTALL
AC_PROG_LN_S

# xsessions data of path for GDM
AC_ARG_WITH([xsession-path],
    AS_HELP_STRING(
        [--with-xsession-path=PATH],
        [set the install path of xsession data [[DATAROOTDIR/xsessions]]]),
        [test x$withval != x && xsesspath="$withval"],
        [xsesspath="\${datarootdir}/xsessions"])
AC_SUBST(xsesspath)

dnl Fix invalid sysconfdir when --prefix=/usr
if test `eval "echo $sysconfdir"` = /usr/etc
then
    sysconfdir=/etc
fi

GETTEXT_PACKAGE=xde-common
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE", [Name of default gettext domain])
AC_SUBST(GETTEXT_PACKAGE)

# Generate po/LINGUAS on the fly rather than relying on translators
# to maintain it manually. This also overcome the problem that Transifex
# cannot add a language to po/LINGUAS if a new po file is submitted.
rm -f $srcdir/po/LINGUAS
for po_file in `ls $srcdir/po/*.po | sort`;
do
    lang=`echo "$po_file" | sed "s|.*/po/\(.*\)\.po|\1|g"`
    echo $lang >> $srcdir/po/LINGUAS
done

AM_GLIB_GNU_GETTEXT

IT_PROG_INTLTOOL([0.40.0])

dnl dirty hack used to prevent the installation of useless mo files.
USE_NLS=no
AC_SUBST(USE_NLS)

AC_OUTPUT([
  Makefile
  startxde
  xde-logout
  XDE.desktop.in
  po/Makefile.in
])

if test x"$sysconfdir" != x'/etc'; then
    echo
    echo
    echo 'Error: sysconfdir is not /etc.'
    echo 'Please consider passing --sysconfdir=/etc to configure.';
    echo 'Otherwise default config files will be installed to wrong place.'
    echo
    echo
fi
