#
#  Octtools 3.0 Makefile
#
#  espresso - two-level minimization
#
#  Makefile created on Sun Feb 26 14:45:52 PST 1989 by octtools (using 'create-octtools-makefile')
#
#  Copyright (c) 1988, 1989, Regents of the University of California
#
#
# Description of the 'targets':
#
#  all:			create the tags file, run lint, build the tool/package
#  install:		build the tool/package and install all the necessary files
#  uninstall:		remove the files that would be installed with 'make install'
#  debug:		build and install the debug versions of the package
#				(for tools, build the debug versions and leave in the
#				source directories; note: debug versions of tools
#				MUST be built using 'make debug' or 'make debug-*')
#  header:		install the exported header files for the package
#  lint:		run lint
#  clean:		remove the binary, object files, and temporary files
#  require:		echo a list of packages used in the compilation of the tool/package
#  toolrequire:		echo a list of tools used in the running of the tool
#  test:		run a simple test on the tool/package
#  tags:		build the 'tags' file (for 'vi')
#  TAGS:		build the 'TAGS' file (for 'emacs')
#  info:		echo a one-line description of the tool/package
#  print:		print out the man page or doc file for the tool/package
#  dist:		dist the tool/package
#  test-dist:		tell what would be disted in 'make dist' were run
#  depend:		generate the dependency information
#  strip-depend:	remove the dependency information
#
#
# Description of the 'variables':
#
#  BUILD:		name of the program that builds a 'Makefile' from
#				'Makefile.template'
#  CAD:			location of the CAD tools (for installation)
#  CADROOT:		run-time location of the CAD libraries (can have '~')
#  CC:			name of the C-compiler
#  COMPFLAG:		compilation level (usually nothing, -g, -pg, or -O)
#  CP:			name of the program used for installation ('cp' for installing
#				the file each time, 'ln -s' for installing a link)
#  LDFLAGS:		flags used for linking (e.g., -lXMenu -lX -lm)
#  LINKER:		name of the program used for linking (normally '${CC}')
#  LINTCREATEFLAG:	flag used by 'lint' for creating lint libraries
#				(-C for BSD, ULTRIX 2.2; -o for IBM RT/PC, ULTRIX 3.0)
#  P:			either nothing or & - used by the sequent to
#				parallelize compiles
#  PRINTER:		name of the printer
#  SHELL:		shell used by 'make' (should always be the bourne shell)
#  UTILS:		location of the utility programs
#
#
#------------------------------------------------------------------------------

# for HPUX
SHELL	= /bin/sh

CAD	= /net/shambhala/users/octtools-3.0
CADROOT	= ~octtools
UTILS	= ${CAD}/utils

LINTCREATEFLAG = -C
COMPFLAG=

# an alternative if you want links in the installation locations
# back to the source directories would be:
#   CP = sh -c 'ln -s `pwd`/$$0 $$1'
CP = cp

BUILD = ${UTILS}/bin/create-octtools-makefile

# alternate (for ULTRIX) would be LINKER = 'ld -N ${CAD}/utils/pageZero/crt0.o'
# (this will not work for -pg programs)
LINKER = ${CC}

# cute hack for the sequent
#   setenv PARALLEL 8; make P="&" install
P = 

NAME	= espresso

# packages required for this package/tool
REQUIRE	= utility mm port

# tools required for this tool
TOOLREQUIRE = 

SRC	= cofactor.c cols.c compl.c contain.c cubestr.c cvrin.c cvrm.c cvrmisc.c cvrout.c dominate.c equiv.c espresso.c essen.c exact.c expand.c gasp.c getopt.c gimpel.c globals.c hack.c indep.c irred.c main.c map.c matrix.c mincov.c opo.c pair.c part.c primes.c reduce.c rows.c set.c setc.c sharp.c sminterf.c solution.c sparse.c unate.c verify.c signature.c signature_exact.c util_signature.c black_white.c canonical.c essentiality.c sigma.c
LSRC	= cofactor.c cols.c compl.c contain.c cubestr.c cvrin.c cvrm.c cvrmisc.c cvrout.c dominate.c equiv.c espresso.c essen.c exact.c expand.c gasp.c getopt.c gimpel.c globals.c hack.c indep.c irred.c main.c map.c matrix.c mincov.c opo.c pair.c part.c primes.c reduce.c rows.c set.c setc.c sharp.c sminterf.c solution.c sparse.c unate.c verify.c signature.c signature_exact.c util_signature.c black_white.c canonical.c essentiality.c sigma.c
OBJ	= cofactor.o cols.o compl.o contain.o cubestr.o cvrin.o cvrm.o cvrmisc.o cvrout.o dominate.o equiv.o espresso.o essen.o exact.o expand.o gasp.o getopt.o gimpel.o globals.o hack.o indep.o irred.o main.o map.o matrix.o mincov.o opo.o pair.o part.o primes.o reduce.o rows.o set.o setc.o sharp.o sminterf.o solution.o sparse.o unate.o verify.o signature.o signature_exact.o util_signature.o black_white.o canonical.o essentiality.o sigma.o
HDR	= espresso.h main.h mincov.h mincov_int.h sparse.h sparse_int.h signature.h

CADBIN	= ${CAD}/bin

TOOLINSTALL= ${CADBIN}/${TARGET} ${CAD}/man/man1/${MAN}
INSTALL	= ${PKGINSTALL} ${TOOLINSTALL} ${CAD}/man/man5/espresso.5 ${CAD}/man/man5/pla.5 ${CAD}/lib/espresso

DISTDEST= ${CAD}/src/${NAME}
DISTHOST= octtools@shambhala
MISC	= Makefile Makefile.template ex examples espresso.5 pla.5

LIBS	= $(CAD)/lib/libutility$(COMPFLAG).a $(CAD)/lib/libst$(COMPFLAG).a $(CAD)/lib/libmm$(COMPFLAG).a $(CAD)/lib/liberrtrap$(COMPFLAG).a $(CAD)/lib/libuprintf$(COMPFLAG).a $(CAD)/lib/libport$(COMPFLAG).a
LINTLIBS= $(CAD)/lib/llib-lutility.ln $(CAD)/lib/llib-lmm.ln $(CAD)/lib/llib-lport.ln

TARGET	= ${NAME}
TARGETG	= ${NAME}-g
TARGETPG	= ${NAME}-pg
MAN	= ${NAME}.1

PRINTER	= lps40
MACROS	= -man.4.3
PRINT	= lpr
TROFF	= ptroff
TBL	= tbl

INCLUDE	= -I${CAD}/include 
CFLAGS	= ${COMPFLAG} ${INCLUDE} '-DCADROOT="${CADROOT}"'
VERSION	= "-DCUR_DATE=\"`date | awk '{print $$2, $$3, $$6}'`\"" \
	  "-DCUR_TIME=\"`date | awk '{print $$4}'`\""
LINTFLAGS= ${INCLUDE} '-DCADROOT="${CADROOT}"'
LDFLAGS	=  -lm

#-----------------------------------------------------------------------

all: tags lint ${TARGET}

build: Makefile.template
	${BUILD} Makefile.template

install: ${INSTALL}

uninstall:
	rm -rf ${INSTALL}

version.o: version.c
	${CC} ${CFLAGS} ${VERSION} -c version.c
	-touch -f version.c

debug: debug-g debug-pg


debug-g:
	rm -f ${OBJ}
	make COMPFLAG=-g CC="${CC}" CAD="${CAD}" CADROOT="${CADROOT}" ${MFLAGS} ${TARGETG}

debug-pg:
	rm -f ${OBJ}
	make COMPFLAG=-pg CC="${CC}" CAD="${CAD}" CADROOT="${CADROOT}" ${MFLAGS} ${TARGETPG}



${TARGET} ${TARGETG} ${TARGETPG}:${P} ${OBJ} ${LIBS}
	${LINKER} ${COMPFLAG} -o $@ ${OBJ} ${LIBS} ${LDFLAGS}


header::

${CADBIN}/${TARGET}: ${TARGET}
	rm -f $@
	${CP} $? $@
	strip $@

${CAD}/man/man1/${MAN}: ${MAN}
	rm -f $@
	${TBL} < $? > $@

lint: ${LSRC} ${DRVRSRC} ${HDR} ${LINTLIBS}
	lint ${LINTFLAGS} ${LSRC} ${DRVRSRC} ${LINTLIBS} ${LDFLAGS} | tee lint

clean::
	rm -f ${OBJ} ${DRVROBJ} ${TARGET} ${TARGETG} ${TARGETPG} ${DRIVER} tags TAGS ${LIB} ${LIBG} ${LIBPG} ${LINTLIB} lint make.out mktemp

require:
	@echo ${REQUIRE}

toolrequire:
	@echo ${TOOLREQUIRE}

test::
	@test -f ${CADBIN}/${TARGET}

tags: ${LSRC} ${DRVRSRC} ${HDR}
	ctags ${LSRC} ${DRVRSRC} ${HDR}

TAGS: ${LSRC} ${DRVRSRC} ${HDR}
	etags ${LSRC} ${DRVRSRC} ${HDR}

info:
	@echo '${NAME}:  two-level minimization'

print:: ${DOC} ${MAN}
	${TBL} < ${MAN} | ${TROFF} -P${PRINTER} ${MACROS}

dist: ${SRC} ${DRVRSRC} ${HDR} ${DOC} ${MAN}
	rdist -Rich ${SRC} ${DRVRSRC} ${HDR} ${DOC} ${MAN} ${MISC} ${DISTHOST}:${DISTDEST}

test-dist: ${SRC} ${DRVRSRC} ${HDR} ${DOC} ${MAN}
	rdist -Richv ${SRC} ${DRVRSRC} ${HDR} ${DOC} ${MAN} ${MISC} ${DISTHOST}:${DISTDEST}


depend: ${SRC} ${DRVRSRC} ${HDR}
	@rm -f mktemp
	@sed '/^#--DO NOT CHANGE ANYTHING AFTER THIS LINE/,$$d' Makefile > mktemp
	@echo '#--DO NOT CHANGE ANYTHING AFTER THIS LINE' >> mktemp
	@${UTILS}/bin/cc-M ${INCLUDE} ${SRC} ${DRVRSRC} | sed 's|${CAD}|$${CAD}|g' >>mktemp
	@mv mktemp Makefile

strip-depend:
	@rm -f mktemp
	@sed '/^#--DO NOT CHANGE ANYTHING AFTER THIS LINE/,$$d' Makefile > mktemp
	@mv mktemp Makefile

# does not work with 'pat2tap' creation of devnames.h
#${SRC} ${DRVRSRC} ${HDR}:
#	co $@

#--EXTRA TARGETS
${CAD}/man/man5/espresso.5: espresso.5
	rm -f $@
	tbl < $? > $@

${CAD}/man/man5/pla.5: pla.5
	rm -f $@
	tbl < $? > $@

${CAD}/lib/espresso: ex
	rm -rf $@
	-mkdir $@
	-cp -r $? $@

test::
	(cd examples; make CAD=${CAD} > ../test.out 2>&1)

clean::
	rm -f test.out

clean::
	(cd examples; make clean)


#--DO NOT CHANGE ANYTHING AFTER THIS LINE
cofactor.o: cofactor.c ${CAD}/include/ansi.h
cofactor.o:  ${CAD}/include/port.h
cofactor.o:  ${CAD}/include/utility.h espresso.h mincov.h
cofactor.o:  sparse.h
cols.o: cols.c ${CAD}/include/ansi.h
cols.o:  ${CAD}/include/port.h
cols.o:  ${CAD}/include/utility.h sparse.h sparse_int.h
compl.o: compl.c ${CAD}/include/ansi.h
compl.o:  ${CAD}/include/port.h
compl.o:  ${CAD}/include/utility.h espresso.h mincov.h
compl.o:  sparse.h
contain.o: contain.c ${CAD}/include/ansi.h
contain.o:  ${CAD}/include/port.h
contain.o:  ${CAD}/include/utility.h espresso.h mincov.h
contain.o:  sparse.h
cubestr.o: cubestr.c ${CAD}/include/ansi.h
cubestr.o:  ${CAD}/include/port.h
cubestr.o:  ${CAD}/include/utility.h espresso.h mincov.h
cubestr.o:  sparse.h
cvrin.o: cvrin.c ${CAD}/include/ansi.h
cvrin.o:  ${CAD}/include/port.h
cvrin.o:  ${CAD}/include/utility.h espresso.h mincov.h
cvrin.o:  sparse.h
cvrm.o: cvrm.c ${CAD}/include/ansi.h
cvrm.o:  ${CAD}/include/port.h
cvrm.o:  ${CAD}/include/utility.h espresso.h mincov.h
cvrm.o:  sparse.h
cvrmisc.o: cvrmisc.c ${CAD}/include/ansi.h
cvrmisc.o:  ${CAD}/include/port.h
cvrmisc.o:  ${CAD}/include/utility.h espresso.h mincov.h
cvrmisc.o:  sparse.h
cvrout.o: cvrout.c ${CAD}/include/ansi.h
cvrout.o:  ${CAD}/include/port.h
cvrout.o:  ${CAD}/include/utility.h espresso.h mincov.h
cvrout.o:  sparse.h
dominate.o: dominate.c ${CAD}/include/ansi.h
dominate.o:  ${CAD}/include/port.h
dominate.o:  ${CAD}/include/utility.h mincov.h mincov_int.h
dominate.o:  sparse.h
equiv.o: equiv.c ${CAD}/include/ansi.h
equiv.o:  ${CAD}/include/port.h
equiv.o:  ${CAD}/include/utility.h espresso.h mincov.h
equiv.o:  sparse.h
espresso.o: espresso.c ${CAD}/include/ansi.h
espresso.o:  ${CAD}/include/port.h
espresso.o:  ${CAD}/include/utility.h espresso.h mincov.h
espresso.o:  sparse.h
essen.o: essen.c ${CAD}/include/ansi.h
essen.o:  ${CAD}/include/port.h
essen.o:  ${CAD}/include/utility.h espresso.h mincov.h
essen.o:  sparse.h
exact.o: exact.c ${CAD}/include/ansi.h
exact.o:  ${CAD}/include/port.h
exact.o:  ${CAD}/include/utility.h espresso.h mincov.h
exact.o:  sparse.h
expand.o: expand.c ${CAD}/include/ansi.h
expand.o:  ${CAD}/include/port.h
expand.o:  ${CAD}/include/utility.h espresso.h mincov.h
expand.o:  sparse.h
gasp.o: gasp.c ${CAD}/include/ansi.h
gasp.o:  ${CAD}/include/port.h
gasp.o:  ${CAD}/include/utility.h espresso.h mincov.h
gasp.o:  sparse.h
getopt.o: getopt.c ${CAD}/include/ansi.h
getopt.o:  ${CAD}/include/port.h
getopt.o:  ${CAD}/include/utility.h
gimpel.o: gimpel.c ${CAD}/include/ansi.h
gimpel.o:  ${CAD}/include/port.h
gimpel.o:  ${CAD}/include/utility.h mincov.h mincov_int.h
gimpel.o:  sparse.h
globals.o: globals.c ${CAD}/include/ansi.h
globals.o:  ${CAD}/include/port.h
globals.o:  ${CAD}/include/utility.h espresso.h mincov.h
globals.o:  sparse.h
hack.o: hack.c ${CAD}/include/ansi.h
hack.o:  ${CAD}/include/port.h
hack.o:  ${CAD}/include/utility.h espresso.h mincov.h
hack.o:  sparse.h
indep.o: indep.c ${CAD}/include/ansi.h
indep.o:  ${CAD}/include/port.h
indep.o:  ${CAD}/include/utility.h mincov.h mincov_int.h
indep.o:  sparse.h
irred.o: irred.c ${CAD}/include/ansi.h
irred.o:  ${CAD}/include/port.h
irred.o:  ${CAD}/include/utility.h espresso.h mincov.h
irred.o:  sparse.h
main.o: main.c ${CAD}/include/ansi.h
main.o:  ${CAD}/include/port.h
main.o:  ${CAD}/include/utility.h espresso.h main.h mincov.h
main.o:  sparse.h
map.o: map.c ${CAD}/include/ansi.h
map.o:  ${CAD}/include/port.h
map.o:  ${CAD}/include/utility.h espresso.h mincov.h sparse.h
matrix.o: matrix.c ${CAD}/include/ansi.h
matrix.o:  ${CAD}/include/port.h
matrix.o:  ${CAD}/include/utility.h sparse.h sparse_int.h
mincov.o: mincov.c ${CAD}/include/ansi.h
mincov.o:  ${CAD}/include/port.h
mincov.o:  ${CAD}/include/utility.h mincov.h mincov_int.h
mincov.o:  sparse.h
opo.o: opo.c ${CAD}/include/ansi.h
opo.o:  ${CAD}/include/port.h
opo.o:  ${CAD}/include/utility.h espresso.h mincov.h sparse.h
pair.o: pair.c ${CAD}/include/ansi.h
pair.o:  ${CAD}/include/port.h
pair.o:  ${CAD}/include/utility.h espresso.h mincov.h
pair.o:  sparse.h
part.o: part.c ${CAD}/include/ansi.h
part.o:  ${CAD}/include/port.h
part.o:  ${CAD}/include/utility.h mincov.h mincov_int.h
part.o:  sparse.h
primes.o: primes.c ${CAD}/include/ansi.h
primes.o:  ${CAD}/include/port.h
primes.o:  ${CAD}/include/utility.h espresso.h mincov.h
primes.o:  sparse.h
reduce.o: reduce.c ${CAD}/include/ansi.h
reduce.o:  ${CAD}/include/port.h
reduce.o:  ${CAD}/include/utility.h espresso.h mincov.h
reduce.o:  sparse.h
rows.o: rows.c ${CAD}/include/ansi.h
rows.o:  ${CAD}/include/port.h
rows.o:  ${CAD}/include/utility.h sparse.h sparse_int.h
set.o: set.c ${CAD}/include/ansi.h
set.o:  ${CAD}/include/port.h
set.o:  ${CAD}/include/utility.h espresso.h mincov.h sparse.h
setc.o: setc.c ${CAD}/include/ansi.h
setc.o:  ${CAD}/include/port.h
setc.o:  ${CAD}/include/utility.h espresso.h mincov.h
setc.o:  sparse.h
sharp.o: sharp.c ${CAD}/include/ansi.h
sharp.o:  ${CAD}/include/port.h
sharp.o:  ${CAD}/include/utility.h espresso.h mincov.h
sharp.o:  sparse.h
sminterf.o: sminterf.c ${CAD}/include/ansi.h
sminterf.o:  ${CAD}/include/port.h
sminterf.o:  ${CAD}/include/utility.h espresso.h mincov.h
sminterf.o:  sparse.h
solution.o: solution.c ${CAD}/include/ansi.h
solution.o:  ${CAD}/include/port.h
solution.o:  ${CAD}/include/utility.h mincov.h mincov_int.h
solution.o:  sparse.h
sparse.o: sparse.c ${CAD}/include/ansi.h
sparse.o:  ${CAD}/include/port.h
sparse.o:  ${CAD}/include/utility.h espresso.h mincov.h
sparse.o:  sparse.h
unate.o: unate.c ${CAD}/include/ansi.h
unate.o:  ${CAD}/include/port.h
unate.o:  ${CAD}/include/utility.h espresso.h mincov.h
unate.o:  sparse.h
verify.o: verify.c ${CAD}/include/ansi.h
verify.o:  ${CAD}/include/port.h
verify.o:  ${CAD}/include/utility.h espresso.h mincov.h
verify.o:  sparse.h
