dnl Process this file with autoconf to produce configure.

dnl configure.ac
dnl Copyright (C) 2005 Free Software Foundation, Inc.
dnl 
dnl This file is part of GNU Classpath.
dnl 
dnl GNU Classpath is free software; you can redistribute it and/or modify
dnl it under the terms of the GNU General Public License as published by
dnl the Free Software Foundation; either version 2, or (at your option)
dnl any later version.
dnl  
dnl GNU Classpath is distributed in the hope that it will be useful, but
dnl WITHOUT ANY WARRANTY; without even the implied warranty of
dnl MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
dnl General Public License for more details.
dnl 
dnl You should have received a copy of the GNU General Public License
dnl along with GNU Classpath; see the file COPYING.  If not, write to the
dnl Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
dnl 02111-1307 USA.

AC_INIT(gjdoc, 0.7.9, [classpath@gnu.org])

AC_PREREQ(2.59)

AM_INIT_AUTOMAKE(tar-ustar)
AC_CONFIG_MACRO_DIR([m4])

AC_DISABLE_STATIC

AC_ARG_WITH([antlr-jar],
  	    AS_HELP_STRING([--with-antlr-jar=file],
			   [Use ANTLR from the specified jar file]),
  [ ANTLR_JAR=$withval ],
  [ ANTLR_JAR="$ANTLR_JAR" ])

AM_PROG_GCJ
AM_PROG_LIBTOOL
AC_PROG_JAR
AC_CHECK_CLASSPATH
AC_PROG_JAVA
AC_PROG_JAVAC
AC_PROG_ANTLR(2,7,1)

AC_SUBST(CLASSPATH)

AC_ARG_ENABLE([xmldoclet],
              AS_HELP_STRING([--enable-xmldoclet],
                             [enable doclet which requires XML]), [
enable_xmldoclet=yes
dnl Check if gnujaxp.jar is in $prefix/share/java and prepend it to the
dnl CLASSPATH.

dnl Check if javax.xml.transform.Transformer is on the CLASSPATH
dnl ... if it is, continue; if not, check if gnujaxp.jar is available and
dnl prepend that to the CLASSPATH.  If gnujaxp.jar is not available, fail.

if test "x$prefix" = "xNONE"
then
  export jaxp_prefix=/usr/local
else
  export jaxp_prefix=$prefix
fi

AC_CHECK_FILE([$jaxp_prefix/share/java/gnujaxp.jar],
  if test -z $CLASSPATH
  then
    export CLASSPATH=$jaxp_prefix/share/java/gnujaxp.jar:.
  else
    export CLASSPATH=$jaxp_prefix/share/java/gnujaxp.jar:$CLASSPATH:.
  fi
)

AC_CHECK_RQRD_CLASS([javax.xml.transform.Transformer])
],
[
jni_linkflag=""
enable_xmldoclet=no
])

dnl We need the java.util.regex package for package matcher and author tag.
AC_CHECK_RQRD_CLASS([java.util.regex.Pattern])

AC_ARG_ENABLE([native],
              AS_HELP_STRING([--enable-native],
                             [enable generation of native binaries]), 
                             [enable_native=$enableval],
                             [enable_native=yes])

if test "x${enable_native}" = "xno"; then
  echo "Native compilation disabled."
else
  if test "x${GCJ}" = "xfalse"; then
    enable_native=no
    echo "Native compilation disabled as gcj has not been found"
  fi
fi

AC_SUBST(jni_linkflag)
AM_CONDITIONAL([ENABLE_XMLDOCLET], [test x${enable_xmldoclet} = xyes])
AM_CONDITIONAL([ENABLE_NATIVE], [test x${enable_native} = xyes])

AC_CONFIG_FILES([gjdoc.sh src/resources/version.properties], [chmod +x gjdoc.sh])

AC_OUTPUT([Makefile docs/Makefile])
