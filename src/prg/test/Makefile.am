#########################################################################
#									#
# Script ID: src/prg/test/Makefile.am					#
# Author: Copyright (C) 2019, 2020  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
#	AutoMake script file to generate txt2manwrap test program.	#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 16/08/2019	MG	1.0.1	First release.				#
# 14/09/2019	MG	1.0.2	Add a verbose Answer file so that the	#
#				lines with automatically generated	#
#				dates can all just be deleted before	#
#				comparison.				#
# 23/10/2020	MG	1.0.3	Do not automatically run the tests. The	#
#				byte level comparison is too stringent,	#
#				a new version of txt2man may produce a	#
#				perfectly fine but slightly different	#
#				man page. (xenial and stretch through	#
#				to focal and buster work OK but groovy	#
#				does not pass these tests.)		#
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


CLEANFILES = *.tmp *.sh *.txt wutconv.1*

