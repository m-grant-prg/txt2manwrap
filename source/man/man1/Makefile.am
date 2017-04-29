#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: ./source/man/man1/Makefile.am				#
# Author: Mark Grant							#
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
#									#
#########################################################################


txt2manwrap.1: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	$(edit) $(srcdir)/$(@F).txt > $@.tmp
	txt2man -t "txt2manwrap" -s 1 -v "txt2manwrap Manual" $@.tmp > $@
	rm -f $@.tmp

txt2manwrap.1: $(srcdir)/txt2manwrap.1.txt

man_MANS = txt2manwrap.1

EXTRA_DIST = $(srcdir)/txt2manwrap.1.txt

CLEANFILES = *.tmp txt2manwrap.1
