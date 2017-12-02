#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: ./source/man/man1/Makefile.am				#
# Author: Copyright (C) 2015-2017  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# Automake script file to generate txt2manwrap manual pages from	#
# source.								#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 19/09/2015	MG	1.0.1	First release.				#
# 29/04/2017	MG	1.0.2	Output from $(edit) was being ignored.	#
#				Rename source file extension .man.in	#
# 02/12/2017	MG	1.0.3	Determine the manual section from the	#
#				target suffix. If the suffix is blank	#
#				(foo.) or if there is no suffix (foo)	#
#				then error out.				#
# 02/12/2017	MG	1.0.4	Add SPDX license tags to source files.	#
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
