## Process this file with automake to produce Makefile.in.

# Makefile.am
# Copyright (C) 2005 Free Software Foundation, Inc.
# 
# This file is part of GNU Classpath.
# 
# GNU Classpath is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#  
# GNU Classpath is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with GNU Classpath; see the file COPYING.  If not, write to the
# Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
# 02111-1307 USA.

TEXIPOD = $(srcdir)/../contrib/texi2pod.pl
POD2MAN = pod2man

dist_man_MANS = gjdoc.1

info_TEXINFOS = gjdoc.texi
gjdoc_TEXINFOS = invoke.texi

EXTRA_DIST = gcc-common.texi fdl.texi gpl.texi

MAKEINFOFLAGS = -I $(srcdir)/contrib/include/ -I $(srcdir)/src/docs

CLEANFILES = gjdoc.pod
MAINTAINERCLEANFILES = stamp-vti version.texi $(dist_man_MANS)

# The following is a neat hack which allows extracting the man page
# from the texinfo manual. Stolen from gcc.

gjdoc.pod: invoke.texi
	$(TEXIPOD) $< >$@

gjdoc.1: invoke.texi $(top_srcdir)/configure.ac
	$(MAKE) $(AM_MAKEFLAGS) gjdoc.pod
	$(POD2MAN) --center="GNU" --release="gjdoc-$(VERSION)" --section=1 --name=gjdoc gjdoc.pod >$@
