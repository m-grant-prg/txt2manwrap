#########################################################################
#									#
# Script ID: ./configure.ac						#
# Author: Copyright (C) 2015-2021  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# Autoconfigure script file to configure txt2manwrap project.		#
#									#
# configure cmd line syntax: ./configure				#
#									#
# Layout: (Only relevant sections will exist).				#
# ChangeLog : High level ChangeLog					#
# SECTION  1: Initialisation & Setup					#
# SECTION  2: Architecture, target and host checks			#
# SECTION  3: Command line arguments					#
# SECTION  4: Compiler setup						#
# SECTION  5: Check for programs					#
# SECTION  6: Check for libraries					#
# SECTION  7: Check for header files					#
# SECTION  8: Check for types						#
# SECTION  9: Check for structures					#
# SECTION 10: Check for compiler characteristics			#
# SECTION 11: Check for library functions				#
# SECTION 12: Check for pkg-config files				#
# SECTION 13: Check for system services					#
# SECTION 14: Additional checks & variables				#
# SECTION 15: Specify the output files					#
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
# 29/04/2017	MG	1.0.3	Make AC_INIT and pkgversion AC_SUBST	#
#				multi-line.				#
#				Fully populate sed variable		#
#				substitution.				#
# 02/12/2017	MG	1.0.4	Add SPDX license tags to source files.	#
# 10/02/2018	MG	1.0.5	Shorten directory names to reduce	#
#				overall path length.			#
#				Update minimum AutoTools version.	#
#				Standardise configure.ac and macro	#
#				directory.				#
# 13/04/2018	MG	1.0.6	Change package versioning to use	#
#				hard-coded value. This is due to the	#
#				use of github which produces source	#
#				tarballs which can be used for package	#
#				generation. These tarballs are used	#
#				outside of git so git versioning is not	#
#				possible, hence the hard-coded value.	#
#				Because of this, other packaging should	#
#				probably use the source tarball rather	#
#				than a dist tarball.			#
# 04/01/2019	MG	1.0.7	Supply Makefiles with edit variable	#
#				with absolute bash path which can be	#
#				substituted in the shebang. Using env	#
#				is OK for non-AutoTools scripts.	#
#				Remove preceding v from package version	#
#				as it should not be there.		#
# 06/01/2019	MG	1.0.8	Remove check for getopt which is not	#
#				used.					#
# 06/02/2019	MG	1.1.1	Add check for getopt after help and	#
#				version CLA introduction.		#
#				Re-vamp to new standard layout.		#
# 16/08/2019	MG	1.1.2	Add test dir for make check.		#
#									#
#########################################################################


#########################################
#					#
# SECTION  1: Initialisation & Setup	#
#					#
#########################################

AC_REVISION([$Revision: 1.1.2 $])

AC_PREREQ([2.69])

#
# The package version in ac init will be used to create an output variable which
# can be used by ac output and / or the sed setup below to substitute bookmarks
# in source files.
#
AC_INIT(txt2man wrapper script, 1.1.13+rc1, m.grant.prg@gmail.com, txt2manwrap)

AC_MSG_NOTICE(initialisation and setup)

AC_SUBST(pkgversion, $PACKAGE_VERSION)

#
# Passes the options to all am files. Puts objects in the sub-directory
# containing the source. Forces tar to use --format=posix in make dist.
# This also checks :-	BSD install	make variable set	mkdir -p
#			gawk
#
AM_INIT_AUTOMAKE([-Wall -Werror subdir-objects tar-pax])

#
# Standard macros will be automatically placed in m4.
# Programmer defined macros should be placed in, say, m4extra which allows us
# to exclude the standard macros from being git tracked. This other directory
# must be specified as an include option in the Makefile.am ACLOCAL_AMFLAGS
# e.g.
# ACLOCAL_AMFLAGS = -I m4 -I m4extra
#
AC_CONFIG_MACRO_DIR([m4])


#########################################
#					#
# SECTION  5: Check for programs	#
#					#
#########################################

AC_MSG_NOTICE(checking for basic programs that have AutoConf checks)

#
# The small set of tools you can expect to find on any machine.
#
# awk		date		grep		od
# basename	diff		join		rm
# cat		dirname		ln		rmdir
# cc		egrep		ls		sed
# chgrp		expr		mkdir		sleep
# chown		expr (‘|’)	mkfifo		sort
# chmod		expr (‘:’)	mknod		tar
# cmp		fgrep		mktemp		touch
# cp		find		mv		tr
#
# (For further information including limitations to the above, see Section 11.15
# in the GNU AutoConf Manual).
#
# If using am init automake, gl early or lt init the following programs are
# automatically checked:-
#
# am init automake
#	BSD install	mkdir -p	gawk
#
# gl early
#	ar	grep	egrep	ranlib
#
# lt init
#	fgrep	ranlib	sed
#
# Basic and AutoTools program checks.
#
AC_PROG_AWK
AC_PROG_EGREP
AC_PROG_FGREP
AC_PROG_GREP
AC_PROG_LN_S
AC_PROG_MKDIR_P
AC_PROG_SED

AC_MSG_NOTICE(checking for some standard AutoTools required programs)
AC_PROG_INSTALL

AC_MSG_NOTICE(checking for particular programs required by this build)
AC_CHECK_PROG([TAR], [tar], [yes], [no])
if test "x$TAR" = "xno" ; then
	AC_MSG_ERROR([tar not found])
fi

AC_CHECK_PROG([TXT2MAN], [txt2man], [yes], [no])
if test "x$TXT2MAN" = "xno" ; then
	AC_MSG_ERROR([txt2man not found])
fi

AC_MSG_NOTICE(checking for particular programs required at build and run time)
AC_PATH_PROG([BASH], [bash], [no])
if test "x$BASH" = "xno" ; then
	AC_MSG_ERROR([bash not found])
fi

AC_MSG_NOTICE(checking for particular programs required at run time)
AC_CHECK_PROG(ECHO, echo, yes, no)
if test "x$ECHO" = "xno" ; then
	AC_MSG_WARN(echo not found - needed at run time)
fi

AC_CHECK_PROG(PRINTF, printf, yes, no)
if test "x$PRINTF" = "xno" ; then
	AC_MSG_WARN(printf not found - needed at run time)
fi

AC_CHECK_PROG([GETOPT], [getopt], [yes], [no])
if test "x$GETOPT" = "xno" ; then
	AC_MSG_WARN(getopt not found - needed at run time)
fi


#################################################
#						#
# SECTION 14: Additional checks & variables	#
#						#
#################################################

AC_MSG_NOTICE(processing additional checks and variables)

#
# Now set up an awk sequence to substitute bookmarks in script files with either
# standard GNU Directory Variables, or with programmer-defined variables set up
# using an AC_SUBST macro above. This awk sequence will be invoked at programmer
# discretion at sub-directory Makefile.am level.
# ----------------------
#
# prefix	/usr/local (typically)
#	exec_prefix	${prefix}
#		bindir	${exec_prefix}/bin	user executables
#		sbindir	${exec_prefix}/sbin	system admin executables
#		libexecdir	${exec_prefix}/libexec	program executables
#		libdir	${exec_prefix}/lib	object code libraries
#	sysconfdir	 ${prefix}/etc	read-only single-machine data
#	sharedstatedir	${prefix}/com	modifiable architecture-independent data
#	localstatedir	${prefix}/var	modifiable single-machine data
#	runstatedir	${localstatedir}/run
#	includedir	${prefix}/include	C header files
#	oldincludedir	$usr/include	C header files
#	datarootdir	${prefix}/share	read-only arch.-independent data root
#		localedir	${datarootdir}/locale	locale-dependent data
#		datadir	${datarootdir}	read-only architecture-independent data
#		mandir	${datarootdir}/man	man documentation
#		infodir	${datarootdir}/info	info documentation
#		docdir	${datarootdir}/doc/${PACKAGE}	documentation root
#			htmldir	${docdir}	html documentation
#			dvidir	${docdir}	dvi documentation
#			pdfdir	${docdir}	pdf documentation
#			psdir	${docdir}	ps documentation
#		lispdir	${datarootdir}/emacs/site-lisp **Often empty, no check**
#	pkgdatadir	${datarootdir}/${PACKAGE}
#	pkgincludedir	${includedir}/${PACKAGE}
#	pkglibdir	${libdir}/${PACKAGE}
#	pkglibexecdir	${libexecdir}/${PACKAGE}
#
AC_SUBST([edit], ["$AWK \
		'{ \
		gsub(/@bashlocation[@]/,"'"$(BASH)"'"); \
		gsub(/@pkgversion[@]/,"'"$(pkgversion)"'"); \
		gsub(/@prefix[@]/,"'"$(prefix)"'"); \
		gsub(/@exec_prefix[@]/,"'"$(exec_prefix)"'"); \
		gsub(/@bindir[@]/,"'"$(bindir)"'"); \
		gsub(/@sbindir[@]/,"'"$(sbindir)"'"); \
		gsub(/@libexecdir[@]/,"'"$(libexecdir)"'"); \
		gsub(/@libdir[@]/,"'"$(libdir)"'"); \
		gsub(/@sysconfdir[@]/,"'"$(sysconfdir)"'"); \
		gsub(/@sharedstatedir[@]/,"'"$(sharedstatedir)"'"); \
		gsub(/@localstatedir[@]/,"'"$(localstatedir)"'"); \
		gsub(/@runstatedir[@]/,"'"$(runstatedir)"'"); \
		gsub(/@includedir[@]/,"'"$(includedir)"'"); \
		gsub(/@oldincludedir[@]/,"'"$(oldincludedir)"'"); \
		gsub(/@datarootdir[@]/,"'"$(datarootdir)"'"); \
		gsub(/@localedir[@]/,"'"$(localedir)"'"); \
		gsub(/@datadir[@]/,"'"$(datadir)"'"); \
		gsub(/@mandir[@]/,"'"$(mandir)"'"); \
		gsub(/@infodir[@]/,"'"$(infodir)"'"); \
		gsub(/@docdir[@]/,"'"$(docdir)"'"); \
		gsub(/@htmldir[@]/,"'"$(htmldir)"'"); \
		gsub(/@dvidir[@]/,"'"$(dvidir)"'"); \
		gsub(/@pdfdir[@]/,"'"$(pdfdir)"'"); \
		gsub(/@psdir[@]/,"'"$(psdir)"'"); \
		gsub(/@pkgdatadir[@]/,"'"$(pkgdatadir)"'"); \
		gsub(/@pkgincludedir[@]/,"'"$(pkgincludedir)"'"); \
		gsub(/@pkglibdir[@]/,"'"$(pkglibdir)"'"); \
		gsub(/@pkglibexecdir[@]/,"'"$(pkglibexecdir)"'"); \
		print ; }'"])


#########################################
#					#
# SECTION 15: Specify the output files	#
#					#
#########################################

AC_MSG_NOTICE(processing output files)

#
# Non-Makefile files to generate.
# AC_CONFIG_FILES should not be used to substitute AutoConf Installation
# Directory Variables, (bindir and friends), except in Makefiles and pkg-config
# files. See GNU AutoConf manual section 4.8.2 Installation Directory Variables.
#

# Project Makefiles to create.
AC_CONFIG_FILES([Makefile
		src/man/1/Makefile
		src/prg/bash/Makefile
		src/prg/test/Makefile])

AC_OUTPUT

