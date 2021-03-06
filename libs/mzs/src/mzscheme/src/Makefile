#
# Makefile for mzscheme basic sources
#

srcdir = .
builddir = .

CC = gcc
PERL = 

MZSRC = $(srcdir)

CFLAGS = -g -O2  -Wall     -I$(builddir)/.. -I$(srcdir)/../include

OBJS =  salloc.o \
	bignum.o \
	bool.o \
	builtin.o \
	char.o \
	complex.o \
	dynext.o \
	env.o \
	error.o \
	eval.o \
	file.o \
	fun.o \
        gmp.o \
	hash.o \
	image.o \
	jit.o \
	list.o \
	module.o \
	network.o \
	numarith.o \
	number.o \
	numcomp.o \
	numstr.o \
	port.o \
	portfun.o \
	print.o \
        rational.o \
	read.o \
	regexp.o \
	sema.o \
	setjmpup.o \
	string.o \
	struct.o \
	stxobj.o \
	symbol.o \
	syntax.o \
	thread.o \
	type.o \
	vector.o  

SRCS =  $(srcdir)/salloc.c \
	$(srcdir)/bignum.c \
	$(srcdir)/bool.c \
	$(srcdir)/builtin.c \
	$(srcdir)/char.c \
	$(srcdir)/complex.c \
	$(srcdir)/dynext.c \
	$(srcdir)/env.c \
	$(srcdir)/error.c \
	$(srcdir)/eval.c \
	$(srcdir)/file.c \
	$(srcdir)/fun.c \
	$(srcdir)/gmp/gmp.c \
	$(srcdir)/hash.c \
	$(srcdir)/image.c \
	$(srcdir)/jit.c \
	$(srcdir)/list.c \
	$(srcdir)/module.c \
	$(srcdir)/network.c \
	$(srcdir)/numarith.c \
	$(srcdir)/number.c \
	$(srcdir)/numcomp.c \
	$(srcdir)/numstr.c \
	$(srcdir)/port.c \
	$(srcdir)/portfun.c \
	$(srcdir)/print.c \
	$(srcdir)/rational.c \
	$(srcdir)/read.c \
	$(srcdir)/regexp.c \
	$(srcdir)/sema.c \
	$(srcdir)/setjmpup.c \
	$(srcdir)/string.c \
	$(srcdir)/struct.c \
	$(srcdir)/stxobj.c \
	$(srcdir)/symbol.c \
	$(srcdir)/syntax.c \
	$(srcdir)/thread.c \
	$(srcdir)/type.c \
	$(srcdir)/vector.c

wrong:
	echo Make from the directory above this one

all:
	$(MAKE) mzheaders
	$(MAKE) mzobjects

mzheaders: $(srcdir)/schemex.h $(srcdir)/schemexm.h $(srcdir)/schemex.inc $(srcdir)/schexn.h schsys.h \
           $(srcdir)/../include/mzscheme.exp $(srcdir)/../include/mzwin.def $(srcdir)/../include/gmzwin.def \
           $(srcdir)/../include/mzscheme3m.exp $(srcdir)/../include/mzwin3m.def 

mzobjects: $(OBJS)

$(srcdir)/startup.inc : $(srcdir)/startup.ss $(srcdir)/sstoinc
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/startup.inc ; else $(PERL) $(srcdir)/sstoinc < $(srcdir)/startup.ss > $(srcdir)/startup.inc ; fi

$(srcdir)/schemex.h : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/schemex.h ; else $(PERL) $(srcdir)/makex < $(srcdir)/schemef.h > $(srcdir)/schemex.h ; fi

$(srcdir)/schemexm.h : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/schemexm.h ; else $(PERL) -s -- $(srcdir)/makex -list < $(srcdir)/schemef.h > $(srcdir)/schemexm.h ; fi

$(srcdir)/schemex.inc : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/schemex.inc ; else $(PERL) -s -- $(srcdir)/makex -assign < $(srcdir)/schemef.h > $(srcdir)/schemex.inc ; fi

$(srcdir)/../include/mzscheme.exp : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/../include/mzscheme.exp ; else $(PERL) -s -- $(srcdir)/makex -exports < $(srcdir)/schemef.h > $(srcdir)/../include/mzscheme.exp ; fi

$(srcdir)/../include/mzscheme3m.exp : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/../include/mzscheme3m.exp ; else $(PERL) -s -- $(srcdir)/makex -exports -precisegc < $(srcdir)/schemef.h > $(srcdir)/../include/mzscheme3m.exp ; fi

$(srcdir)/../include/mzwin.def : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/../include/mzwin.def ; else $(PERL) -s -- $(srcdir)/makex -winex < $(srcdir)/schemef.h > $(srcdir)/../include/mzwin.def ; fi

$(srcdir)/../include/mzwin3m.def : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/../include/mzwin3m.def ; else $(PERL) -s -- $(srcdir)/makex -winex -gwinex -precisegc < $(srcdir)/schemef.h > $(srcdir)/../include/mzwin3m.def ; fi

$(srcdir)/../include/gmzwin.def : $(srcdir)/schemef.h $(srcdir)/makex
	if [ "$(PERL)" = '' ] ; then touch $(srcdir)/../include/gmzwin.def ; else $(PERL) -s -- $(srcdir)/makex -gwinex < $(srcdir)/schemef.h > $(srcdir)/../include/gmzwin.def ; fi

schsys.h : $(srcdir)/sysname
	echo -n "#define SCHEME_PLATFORM_LIBRARY_SUBPATH " > schsys.h
	$(srcdir)/sysname >> schsys.h

depend:
	makedepend -- $(CFLAGS) -- $(SRCS)

clean:
	/bin/rm -f *.o schsys.h

salloc.o: $(srcdir)/salloc.c
	$(CC) $(CFLAGS) -c $(srcdir)/salloc.c -o salloc.o
bignum.o: $(srcdir)/bignum.c $(srcdir)/bgnfloat.inc
	$(CC) $(CFLAGS) -c $(srcdir)/bignum.c -o bignum.o
bool.o: $(srcdir)/bool.c
	$(CC) $(CFLAGS) -c $(srcdir)/bool.c -o bool.o
builtin.o: $(srcdir)/builtin.c
	$(CC) $(CFLAGS) -c $(srcdir)/builtin.c -o builtin.o
char.o: $(srcdir)/char.c
	$(CC) $(CFLAGS) -c $(srcdir)/char.c -o char.o
complex.o: $(srcdir)/complex.c
	$(CC) $(CFLAGS) -c $(srcdir)/complex.c -o complex.o
dynext.o: $(srcdir)/dynext.c
	$(CC) $(CFLAGS) -c $(srcdir)/dynext.c -o dynext.o
env.o: $(srcdir)/env.c
	$(CC) $(CFLAGS) -c $(srcdir)/env.c -o env.o
error.o: $(srcdir)/error.c
	$(CC) $(CFLAGS) -c $(srcdir)/error.c -o error.o
eval.o: $(srcdir)/eval.c $(srcdir)/schapp.inc $(srcdir)/schnapp.inc
	$(CC) $(CFLAGS) -c $(srcdir)/eval.c -o eval.o
file.o: $(srcdir)/file.c
	$(CC) $(CFLAGS) -c $(srcdir)/file.c -o file.o
fun.o: $(srcdir)/fun.c
	$(CC) $(CFLAGS) -c $(srcdir)/fun.c -o fun.o
gmp.o: $(srcdir)/gmp/gmp.c $(srcdir)/gmp/gmplonglong.h
	$(CC) $(CFLAGS) -c $(srcdir)/gmp/gmp.c -o gmp.o
hash.o: $(srcdir)/hash.c
	$(CC) $(CFLAGS) -c $(srcdir)/hash.c -o hash.o
image.o: $(srcdir)/image.c
	$(CC) $(CFLAGS) -c $(srcdir)/image.c -o image.o
jit.o: $(srcdir)/jit.c
	$(CC) $(CFLAGS) -c $(srcdir)/jit.c -o jit.o
list.o: $(srcdir)/list.c
	$(CC) $(CFLAGS) -c $(srcdir)/list.c -o list.o
module.o: $(srcdir)/module.c
	$(CC) $(CFLAGS) -c $(srcdir)/module.c -o module.o
network.o: $(srcdir)/network.c
	$(CC) $(CFLAGS) -c $(srcdir)/network.c -o network.o
numarith.o: $(srcdir)/numarith.c
	$(CC) $(CFLAGS) -c $(srcdir)/numarith.c -o numarith.o
number.o: $(srcdir)/number.c
	$(CC) $(CFLAGS) -c $(srcdir)/number.c -o number.o
numcomp.o: $(srcdir)/numcomp.c
	$(CC) $(CFLAGS) -c $(srcdir)/numcomp.c -o numcomp.o
numstr.o: $(srcdir)/numstr.c
	$(CC) $(CFLAGS) -c $(srcdir)/numstr.c -o numstr.o
port.o: $(srcdir)/port.c
	$(CC) $(CFLAGS) -c $(srcdir)/port.c -o port.o
portfun.o: $(srcdir)/portfun.c
	$(CC) $(CFLAGS) -c $(srcdir)/portfun.c -o portfun.o
print.o: $(srcdir)/print.c
	$(CC) $(CFLAGS) -c $(srcdir)/print.c -o print.o
rational.o: $(srcdir)/rational.c $(srcdir)/ratfloat.inc
	$(CC) $(CFLAGS) -c $(srcdir)/rational.c -o rational.o
read.o: $(srcdir)/read.c
	$(CC) $(CFLAGS) -c $(srcdir)/read.c -o read.o
regexp.o: $(srcdir)/regexp.c
	$(CC) $(CFLAGS) -c $(srcdir)/regexp.c -o regexp.o
sema.o: $(srcdir)/sema.c
	$(CC) $(CFLAGS) -c $(srcdir)/sema.c -o sema.o
setjmpup.o: $(srcdir)/setjmpup.c
	$(CC) $(CFLAGS) -c $(srcdir)/setjmpup.c -o setjmpup.o
string.o: $(srcdir)/string.c
	$(CC) $(CFLAGS) -c $(srcdir)/string.c -I. -o string.o
struct.o: $(srcdir)/struct.c
	$(CC) $(CFLAGS) -c $(srcdir)/struct.c -o struct.o
stxobj.o: $(srcdir)/stxobj.c
	$(CC) $(CFLAGS) -c $(srcdir)/stxobj.c -o stxobj.o
symbol.o: $(srcdir)/symbol.c
	$(CC) $(CFLAGS) -c $(srcdir)/symbol.c -o symbol.o
syntax.o: $(srcdir)/syntax.c
	$(CC) $(CFLAGS) -c $(srcdir)/syntax.c -o syntax.o
thread.o: $(srcdir)/thread.c
	$(CC) $(CFLAGS) -c $(srcdir)/thread.c -o thread.o
type.o: $(srcdir)/type.c
	$(CC) $(CFLAGS) -c $(srcdir)/type.c -o type.o
vector.o: $(srcdir)/vector.c
	$(CC) $(CFLAGS) -c $(srcdir)/vector.c -o vector.o

gmp_alpha_gcc.o: $(srcdir)/gmp/gmp_alpha_gcc.s
	$(AS) -o gmp_alpha_gcc.o $(srcdir)/gmp/gmp_alpha_gcc.s

SCONFIG =   $(srcdir)/../sconfig.h $(srcdir)/../uconfig.h

# More dependencies

salloc.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
            $(srcdir)/../gc/gc.h $(srcdir)/mzmark.c
bignum.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
          $(srcdir)/../src/stypes.h    
bool.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
          $(srcdir)/../src/stypes.h $(srcdir)/mzeqchk.inc
builtin.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h  \
        $(srcdir)/../src/stypes.h  $(srcdir)/schminc.h $(srcdir)/startup.inc $(srcdir)/cstartup.inc
char.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  $(srcdir)/schuchar.inc
complex.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h  \
         $(srcdir)/../src/stypes.h    
dynext.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h  \
         $(srcdir)/../src/stypes.h $(srcdir)/../src/schemex.h \
         $(srcdir)/schvers.h $(srcdir)/../gc/gc.h $(srcdir)/schemex.h
env.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h  \
        $(srcdir)/../src/stypes.h  $(srcdir)/schminc.h $(srcdir)/mzmark.c
error.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  
eval.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c \
          $(srcdir)/schmach.h $(srcdir)/mzstkchk.h $(srcdir)/schrunst.h
file.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c 
fun.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c $(srcdir)/schmap.inc
hash.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  
image.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  $(srcdir)/schvers.h
jit.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  $(srcdir)/schvers.h $(srcdir)/codetab.inc $(srcdir)/mzmark.c \
        $(srcdir)/lightning/i386/core.h $(srcdir)/lightning/i386/core-common.h \
        $(srcdir)/lightning/i386/asm.h $(srcdir)/lightning/i386/asm-common.h \
        $(srcdir)/lightning/ppc/core.h $(srcdir)/lightning/ppc/core-common.h \
        $(srcdir)/lightning/ppc/asm.h $(srcdir)/lightning/ppc/asm-common.h
list.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  
module.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/schfd.h $(srcdir)/mzmark.c
network.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  $(srcdir)/schfd.h $(srcdir)/mzmark.c
numarith.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/nummacs.h
number.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/nummacs.h
numcomp.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/nummacs.h
numstr.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h  $(srcdir)/random.inc $(srcdir)/newrandom.inc
port.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h  $(srcdir)/schfd.h $(srcdir)/mzmark.c
portfun.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/schfd.h $(srcdir)/mzmark.c
print.o: $(srcdir)/../include/scheme.h $(srcdir)/../src/stypes.h $(srcdir)/../src/schcpt.h \
          $(srcdir)/schpriv.h $(srcdir)/schexn.h $(srcdir)/schvers.h $(SCONFIG) $(srcdir)/mzmark.c
thread.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h  $(srcdir)/schfd.h $(srcdir)/mzmark.c
rational.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h    
read.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/schcpt.h $(srcdir)/schvers.h $(srcdir)/schminc.h \
        $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c
regexp.o:  $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c $(srcdir)/schrx.h
setjmpup.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h   $(srcdir)/schmach.h
string.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h    $(srcdir)/schvers.h $(srcdir)/mzmark.c $(srcdir)/strops.inc \
         $(srcdir)/schustr.inc
struct.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c
stxobj.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/schfd.h $(srcdir)/mzmark.c
symbol.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h   
syntax.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c
sema.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c
type.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
        $(srcdir)/../src/stypes.h $(srcdir)/mzmark.c
vector.o: $(srcdir)/schpriv.h $(srcdir)/schexn.h $(SCONFIG) $(srcdir)/../include/scheme.h \
         $(srcdir)/../src/stypes.h
