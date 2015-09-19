#! /usr/bin/env bash
##########################################################################
##									##
## Script ID: ./source/man/man1/Makefile.am				##
## Author: Mark Grant							##
##									##
## Purpose:								##
## Automake script file to generate txt2manwrap manual pages from	##
## source.								##
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


txt2manwrap.1: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	$(edit) $(srcdir)/$(@F).txt > $@.tmp
	mv $@.tmp $@
	$(srcdir)/cnv2man $(@F) 1 "txt2manwrap Manual" $(srcdir)/$(@F).txt $@
	rm -f $@.tmp

txt2manwrap.1: $(srcdir)/txt2manwrap.1.txt

man_MANS = txt2manwrap.1

EXTRA_DIST = $(srcdir)/txt2manwrap.1.txt $(srcdir)/cnv2man

CLEANFILES = *.tmp txt2manwrap.1

