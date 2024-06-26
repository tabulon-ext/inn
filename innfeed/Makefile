include ../Makefile.global

top	      = ..
CFLAGS	      = $(GCFLAGS) $(SASLINC)

ALL	      = innfeed procbatch imapfeed

SOURCES	      = article.c buffer.c config_l.c config_y.c connection.c endpoint.c \
		host.c imap_connection.c innlistener.c main.c misc.c \
		tape.c

INCLUDES      = article.h buffer.h configfile.h config_y.h connection.h \
		endpoint.h host.h innfeed.h innlistener.h misc.h tape.h

# The objects linked into innfeed.  All SOURCES except connection.o or
# imap_connection.o.
OBJECTS	      = article.o buffer.o config_l.o config_y.o endpoint.o host.o \
		innlistener.o main.o misc.o tape.o

all: $(ALL)

warnings:
	$(MAKE) COPT="$(COPT) $(WARNINGS)" all

install: all
	$(LI_XPRI) innfeed $D$(PATHBIN)/innfeed
	$(LI_XPRI) imapfeed $D$(PATHBIN)/imapfeed
	$(CP_XPRI) procbatch $D$(PATHBIN)/procbatch

bootstrap: config_y.c config_y.h config_l.c

clean:
	rm -f *.o $(ALL)
	rm -f innfeedp
	rm -rf .libs

clobber distclean: clean
	rm -f y.tab.c y.tab.h lex.yy.c

maintclean: distclean
	rm -f config_l.c config_y.c config_y.h

$(FIXSCRIPT):
	@echo Run configure before running make.  See INSTALL for details.
	@exit 1

FIX	= $(SHELL) $(FIXSCRIPT)

##  Compilation rules.

INNFEEDLIBS	= $(LIBSTORAGE) $(LIBHIST) $(LIBINN) $(STORAGE_LIBS) $(LIBS)

config_y.c config_y.h: configfile.y
	$(YACC) -d configfile.y
	mv y.tab.h config_y.h
	mv y.tab.c config_y.c
	touch config_y.h

config_y.h: config_y.c

config_l.c: configfile.l
	$(LEX) $?
	mv lex.yy.c config_l.c

imap_connection.o: imap_connection.c
	$(CC) $(CFLAGS) $(SASL_CPPFLAGS) -c $<

innfeed: $(OBJECTS) connection.o $(LIBSTORAGE) $(LIBINN)
	$(LIBLD) $(LDFLAGS) -o $@ $(OBJECTS) connection.o $(INNFEEDLIBS)

imapfeed: $(OBJECTS) imap_connection.o $(LIBSTORAGE) $(LIBINN)
	$(LIBLD) $(LDFLAGS) -o $@ $(OBJECTS) imap_connection.o \
	    $(SASL_LDFLAGS) $(SASL_LIBS) $(INNFEEDLIBS)

procbatch: procbatch.in $(FIXSCRIPT)
	$(FIX) procbatch.in

tst: config_y.c config_l.c
	gcc -DWANT_MAIN -o tst -g -Wall config_y.c config_l.c -ly -ll

$(LIBINN):	; (cd ../lib ; $(MAKE))
$(LIBSTORAGE):	; (cd ../storage ; $(MAKE) library)
$(LIBHIST):	; (cd ../history ; $(MAKE))


##  Profiling.  These rules have not been checked for a while and may need
##  some work.

profiled: innfeedp

innfeedp: $(SOURCES)
	rm -f $(OBJECTS)
	$(MAKEPROFILING) innfeed
	mv innfeed innfeedp
	rm -f $(OBJECTS)


##  Dependencies.  Default list, below, is probably good enough.

depend: Makefile $(SOURCES)
	$(MAKEDEPEND) '$(CFLAGS)' $(SOURCES)

# DO NOT DELETE THIS LINE -- make depend depends on it.
article.o: article.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/portable/mmap.h \
  ../include/inn/libinn.h ../include/inn/concat.h \
  ../include/inn/portable-stdbool.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h ../include/inn/storage.h \
  ../include/inn/options.h article.h misc.h buffer.h endpoint.h
buffer.o: buffer.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/inn/libinn.h ../include/inn/concat.h \
  ../include/inn/portable-stdbool.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h buffer.h misc.h
config_l.o: config_l.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/inn/libinn.h ../include/inn/concat.h \
  ../include/inn/portable-stdbool.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h configfile.h config_y.h \
  misc.h
config_y.o: config_y.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/inn/libinn.h ../include/inn/concat.h \
  ../include/inn/portable-stdbool.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h configfile.h misc.h
connection.o: connection.c ../include/portable/system.h \
  ../include/config.h ../include/inn/macros.h \
  ../include/inn/portable-macros.h ../include/inn/options.h \
  ../include/inn/system.h ../include/portable/stdbool.h \
  ../include/portable/macros.h ../include/portable/stdbool.h innfeed.h \
  ../include/inn/timer.h ../include/inn/macros.h \
  ../include/portable/socket.h ../include/portable/getaddrinfo.h \
  ../include/portable/getnameinfo.h ../include/inn/fdflag.h \
  ../include/inn/portable-socket.h ../include/inn/portable-stdbool.h \
  ../include/inn/innconf.h ../include/inn/libinn.h ../include/inn/concat.h \
  ../include/inn/xmalloc.h ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h ../include/inn/network.h article.h misc.h \
  buffer.h configfile.h connection.h endpoint.h host.h
endpoint.o: endpoint.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/portable/socket.h \
  ../include/portable/getaddrinfo.h ../include/portable/getnameinfo.h \
  ../include/inn/innconf.h ../include/inn/portable-stdbool.h \
  ../include/inn/libinn.h ../include/inn/concat.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h buffer.h misc.h configfile.h endpoint.h host.h
host.o: host.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/portable/socket.h \
  ../include/portable/getaddrinfo.h ../include/portable/getnameinfo.h \
  ../include/inn/innconf.h ../include/inn/portable-stdbool.h \
  ../include/inn/libinn.h ../include/inn/concat.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h ../include/inn/network.h \
  ../include/inn/portable-socket.h ../include/inn/version.h article.h \
  misc.h buffer.h configfile.h connection.h endpoint.h host.h \
  innlistener.h tape.h
imap_connection.o: imap_connection.c ../include/portable/system.h \
  ../include/config.h ../include/inn/macros.h \
  ../include/inn/portable-macros.h ../include/inn/options.h \
  ../include/inn/system.h ../include/portable/stdbool.h \
  ../include/portable/macros.h ../include/portable/stdbool.h \
  ../include/portable/socket.h ../include/portable/getaddrinfo.h \
  ../include/portable/getnameinfo.h ../include/inn/libinn.h \
  ../include/inn/concat.h ../include/inn/macros.h \
  ../include/inn/portable-stdbool.h ../include/inn/xmalloc.h \
  ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h article.h misc.h buffer.h configfile.h \
  connection.h endpoint.h host.h innfeed.h ../include/inn/timer.h
innlistener.o: innlistener.c ../include/portable/system.h \
  ../include/config.h ../include/inn/macros.h \
  ../include/inn/portable-macros.h ../include/inn/options.h \
  ../include/inn/system.h ../include/portable/stdbool.h \
  ../include/portable/macros.h ../include/portable/stdbool.h innfeed.h \
  ../include/inn/timer.h ../include/inn/macros.h ../include/inn/libinn.h \
  ../include/inn/concat.h ../include/inn/portable-stdbool.h \
  ../include/inn/xmalloc.h ../include/inn/system.h ../include/inn/xwrite.h \
  ../include/inn/messages.h ../include/inn/nntp.h article.h misc.h \
  buffer.h configfile.h endpoint.h host.h innlistener.h tape.h
main.o: main.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/portable/socket.h \
  ../include/portable/getaddrinfo.h ../include/portable/getnameinfo.h \
  ../include/portable/socket-unix.h ../include/inn/innconf.h \
  ../include/inn/portable-stdbool.h ../include/inn/libinn.h \
  ../include/inn/concat.h ../include/inn/xmalloc.h ../include/inn/system.h \
  ../include/inn/xwrite.h ../include/inn/messages.h \
  ../include/inn/storage.h ../include/inn/options.h \
  ../include/inn/version.h article.h misc.h buffer.h configfile.h \
  connection.h endpoint.h host.h innlistener.h tape.h
misc.o: misc.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/inn/innconf.h \
  ../include/inn/portable-stdbool.h ../include/inn/libinn.h \
  ../include/inn/concat.h ../include/inn/xmalloc.h ../include/inn/system.h \
  ../include/inn/xwrite.h ../include/inn/messages.h endpoint.h misc.h \
  tape.h
tape.o: tape.c ../include/portable/system.h ../include/config.h \
  ../include/inn/macros.h ../include/inn/portable-macros.h \
  ../include/inn/options.h ../include/inn/system.h \
  ../include/portable/stdbool.h ../include/portable/macros.h \
  ../include/portable/stdbool.h innfeed.h ../include/inn/timer.h \
  ../include/inn/macros.h ../include/inn/innconf.h \
  ../include/inn/portable-stdbool.h ../include/inn/libinn.h \
  ../include/inn/concat.h ../include/inn/xmalloc.h ../include/inn/system.h \
  ../include/inn/xwrite.h ../include/inn/messages.h article.h misc.h \
  configfile.h endpoint.h host.h tape.h
