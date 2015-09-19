#! /usr/bin/env bash
##########################################################################
##									##
## Script ID: ./source/scripts/Makefile.am				##
## Author: Mark Grant							##
##									##
## Purpose:								##
## Automake script file to generate txt2manwrap scripts from source.	##
##									##
##########################################################################

##########################################################################
##									##
## Changelog								##
##									##
## Date		Author	Version	Description				##
##									##
## 19/09/2015	MG	1.0.1	First release.				##
##									##
##########################################################################


txt2manwrap: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).in >$@.tmp

	mv $@.tmp $@

	chmod a+x $@

txt2manwrap: $(srcdir)/txt2manwrap.in

bin_SCRIPTS = txt2manwrap

EXTRA_DIST = $(srcdir)/txt2manwrap.in

CLEANFILES = *.tmp txt2manwrap

