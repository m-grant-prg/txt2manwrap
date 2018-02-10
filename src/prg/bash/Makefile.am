#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: src/prg/bash/Makefile.am					#
# Author: Copyright (C) 2015-2018  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# Automake script file to generate txt2manwrap scripts from source.	#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 19/09/2015	MG	1.0.1	First release.				#
# 23/10/2015	MG	1.0.2	Restructure to conform to AutoTools	#
#				General Template v1.0.6.		#
# 29/04/2017	MG	1.0.3	Rename bash source file extensions	#
#				.sh.in					#
# 02/12/2017	MG	1.0.4	Add SPDX license tags to source files.	#
# 10/02/2018	MG	1.0.5	Change file's header for new directory	#
#				names.					#
#									#
#########################################################################


txt2manwrap: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.sh.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).sh.in > $@.tmp
	mv $@.tmp $@
	chmod a+x $@
txt2manwrap: $(srcdir)/txt2manwrap.sh.in

bin_SCRIPTS = txt2manwrap

EXTRA_DIST = $(srcdir)/txt2manwrap.sh.in

CLEANFILES = *.tmp txt2manwrap
