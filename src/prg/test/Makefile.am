#########################################################################
#									#
# Author: Copyright (C) 2019-2021, 2023  Mark Grant			#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
#	AutoMake script file to generate txt2manwrap test program.	#
#									#
#########################################################################


Test01Answer.txt Test01verboseAnswer.txt wutconv.1.man: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	cp $${srcdir}$(@F).in  $@
Test01Answer.txt: $(srcdir)/Test01Answer.txt.in
Test01verboseAnswer.txt: $(srcdir)/Test01verboseAnswer.txt.in
wutconv.1.man: $(srcdir)/wutconv.1.man.in

check_DATA = Test01Answer.txt Test01verboseAnswer.txt wutconv.1.man


test01.sh test01verbose.sh test-menu.sh: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).in > $@.tmp
	mv $@.tmp $@
	chmod a+x $@
test01.sh: $(srcdir)/test01.sh.in
test01verbose.sh: $(srcdir)/test01verbose.sh.in
test-menu.sh: $(srcdir)/test-menu.sh.in

check_SCRIPTS = test01.sh test01verbose.sh test-menu.sh


EXTRA_DIST = $(srcdir)/wutconv.1.man.in \
	$(srcdir)/Test01Answer.txt.in $(srcdir)/Test01verboseAnswer.txt.in \
	$(srcdir)/test01.sh.in $(srcdir)/test01verbose.sh.in \
	$(srcdir)/test-menu.sh.in


CLEANFILES = *.tmp *.log *.sh *.trs *.txt wutconv.1*

