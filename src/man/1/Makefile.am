#########################################################################
#									#
# Author: Copyright (C) 2015-2019, 2021, 2023  Mark Grant		#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
# Automake script file to generate txt2manwrap manual pages from	#
# source.								#
#									#
#########################################################################


txt2manwrap.1: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	$(edit) $(srcdir)/$(@F).man.in > $@.tmp
	targfile=$(@F);	\
	if [[ $$targfile == *"."* ]]; then \
		if [[ $${targfile##*.} == "" ]]; then \
			echo "Source file suffix used as section but empty."; \
			exit 1; \
		else \
			section=$${targfile##*.}; \
		fi; \
	else \
		echo "Source file suffix used as section but no dot & empty."; \
		exit 1; \
	fi; \
	txt2man -t "txt2manwrap" -s $$section -v "txt2manwrap Manual" \
		$@.tmp > $@
	rm -f $@.tmp

txt2manwrap.1: $(srcdir)/txt2manwrap.1.man.in

man_MANS = txt2manwrap.1

EXTRA_DIST = $(srcdir)/txt2manwrap.1.man.in

CLEANFILES = *.tmp txt2manwrap.1

