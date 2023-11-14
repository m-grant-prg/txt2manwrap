#########################################################################
#									#
# Author: Copyright (C) 2015-2019, 2021, 2023  Mark Grant		#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
# Automake script file to generate txt2manwrap scripts from source.	#
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

