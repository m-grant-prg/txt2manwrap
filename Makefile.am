#########################################################################
#									#
# Script ID: ./Makefile.am						#
# Author: Copyright (C) 2015-2019  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# Automake script file to generate txt2manwrap project from source.	#
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
# 02/12/2017	MG	1.0.3	Add SPDX license tags to source files.	#
# 10/02/2018	MG	1.0.4	Shorten directory names to reduce	#
#				overall path length.			#
#				Add standard macro directory.		#
# 13/04/2018	MG	1.0.5	Add srctarball target to build a source	#
#				tarball in the build directory. Uses	#
#				git archive to archive HEAD.		#
# 10/06/2018	MG	1.0.6	Add info messages to srctarball target.	#
# 01/11/2018	MG	1.0.7	Change srctarball target to build with	#
#				src between package name and version in	#
#				filename.				#
# 05/01/2019	MG	1.0.8	Change source tarball name to be the	#
#				same as that in GitHub releases. This	#
#				aids integrating with rpm generation.	#
# 11/01/2019	MG	1.0.9	Add install of standard top level GNU	#
#				files AUTHOR, etc.			#
#				Remove unnecessary (ignored) shebang.	#
# 16/08/2019	MG	1.0.10	Add test dir for make check.		#
#									#
#########################################################################


ACLOCAL_AMFLAGS = -I m4


SUBDIRS = src/man/1 src/prg/bash src/prg/test

doc_DATA = AUTHORS ChangeLog COPYING NEWS README

srctarball:
	@cwd="$${PWD}" && \
	targ="$${cwd}/@PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz" && \
	cd @srcdir@ && \
	echo "making srctarball from @srcdir@" && \
	echo "GA	$${targ}" && \
	git archive --format=tar.gz \
		--prefix=@PACKAGE_TARNAME@-@PACKAGE_VERSION@/ \
		--output=$${targ} \
		HEAD && \
	cd -

EXTRA_DIST = $(srcdir)/AUTHORS $(srcdir)/ChangeLog $(srcdir)/COPYING \
		$(srcdir)/NEWS $(srcdir)/README

