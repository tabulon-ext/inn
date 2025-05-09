##  This Makefile contains rules to generate the files derived from POD
##  source.  Normal make commands at the top level of the source tree don't
##  recurse into this directory.  These targets are only used by
##  maintainers.

include ../../Makefile.global

TEXT	= ../../HACKING ../../INSTALL ../../NEWS ../../README ../hook-perl \
	../hook-python ../external-auth ../checklist

MAN1	= ../man/convdate.1 ../man/fastrm.1 ../man/gencancel.1 \
	../man/getlist.1 \
	../man/grephistory.1 ../man/inews.1 ../man/innconfval.1 \
	../man/innmail.1 ../man/nntpget.1 ../man/pullnews.1 ../man/rnews.1 \
	../man/shrinkfile.1 ../man/simpleftp.1

MAN3	= ../man/libinn.3 ../man/libinn_clientlib.3 ../man/libinn_dbz.3 \
	../man/libinn_inndcomm.3 \
	../man/libinnauth.3 ../man/libinnhist.3 ../man/libinnstorage.3 \
	../man/libinn_list.3 ../man/libinn_qio.3 \
	../man/libinn_tst.3 ../man/libinn_uwildmat.3

MAN5	= ../man/active.5 ../man/active.times.5 ../man/buffindexed.conf.5 \
	../man/control.ctl.5 ../man/cycbuff.conf.5 ../man/distrib.pats.5 \
	../man/distributions.5 ../man/expire.ctl.5 ../man/history.5 \
	../man/incoming.conf.5 ../man/inn.conf.5 ../man/innfeed.conf.5 \
	../man/innreport.conf.5 ../man/inn-secrets.conf.5 \
	../man/innwatch.ctl.5 ../man/moderators.5 \
	../man/motd.news.5 ../man/newsfeeds.5 ../man/newsgroups.5 \
	../man/newslog.5 ../man/nnrpd.track.5 ../man/nntpsend.ctl.5 \
	../man/ovdb.5 ../man/ovsqlite.5 \
	../man/passwd.nntp.5 ../man/inn-radius.conf.5 ../man/readers.conf.5 \
	../man/storage.conf.5 ../man/subscriptions.5

MAN8	= ../man/actsync.8 ../man/archive.8 ../man/auth_krb5.8 \
	../man/batcher.8 ../man/buffchan.8 \
	../man/ckpasswd.8 ../man/cnfsheadconf.8 ../man/cnfsstat.8 \
	../man/controlchan.8 ../man/ctlinnd.8 ../man/cvtbatch.8 \
	../man/docheckgroups.8 \
	../man/domain.8 ../man/expire.8 ../man/expireover.8 \
	../man/expirerm.8 ../man/ident.8 \
	../man/innbind.8 ../man/inncheck.8 ../man/innd.8 ../man/inndf.8 \
	../man/innfeed.8 ../man/innreport.8 ../man/innstat.8 \
	../man/innupgrade.8 \
	../man/innwatch.8 ../man/innxbatch.8 ../man/innxmit.8 \
	../man/makedbz.8 ../man/makehistory.8 ../man/mod-active.8 \
	../man/news.daily.8 ../man/news2mail.8 ../man/ninpaths.8 \
	../man/nnrpd.8 ../man/nntpsend.8 \
	../man/ovdb_init.8 ../man/ovdb_monitor.8 ../man/ovdb_server.8 \
	../man/ovdb_stat.8 ../man/overchan.8 ../man/ovsqlite-server.8 \
	../man/ovsqlite-util.8 \
	../man/procbatch.8 ../man/prunehistory.8 ../man/radius.8 \
	../man/rc.news.8 ../man/scanlogs.8 ../man/scanspool.8 \
	../man/send-ihave.8 ../man/sendinpaths.8 ../man/shlock.8 ../man/sm.8 \
	../man/tally.control.8 ../man/tdx-util.8 \
	../man/tinyleaf.8 ../man/writelog.8

ALL	= $(TEXT) $(MAN1) $(MAN3) $(MAN5) $(MAN8)

all bootstrap: $(ALL)

clean clobber distclean:

maintclean: distclean
	rm -f $(ALL)

../../HACKING:		hacking.pod		; $(POD2TEXT) $? > $@
../../INSTALL:		install.pod		; $(POD2TEXT) $? > $@
../../NEWS:		news.pod		; $(POD2TEXT) $? > $@
../../README:		../../readme.pod	; $(POD2TEXT) $? > $@
../checklist:		checklist.pod		; $(POD2TEXT) $? > $@
../external-auth:	external-auth.pod	; $(POD2TEXT) $? > $@
../hook-perl:		hook-perl.pod		; $(POD2TEXT) $? > $@
../hook-python:		hook-python.pod		; $(POD2TEXT) $? > $@

../man/convdate.1:	convdate.pod		; $(POD2MAN) -s 1 $? > $@
../man/fastrm.1:	fastrm.pod		; $(POD2MAN) -s 1 $? > $@
../man/gencancel.1:	gencancel.pod		; $(POD2MAN) -s 1 $? > $@
../man/getlist.1:	getlist.pod		; $(POD2MAN) -s 1 $? > $@
../man/grephistory.1:	grephistory.pod		; $(POD2MAN) -s 1 $? > $@
../man/inews.1:		inews.pod		; $(POD2MAN) -s 1 $? > $@
../man/innconfval.1:	innconfval.pod		; $(POD2MAN) -s 1 $? > $@
../man/innmail.1:	innmail.pod		; $(POD2MAN) -s 1 $? > $@
../man/nntpget.1:	nntpget.pod		; $(POD2MAN) -s 1 $? > $@
../man/pullnews.1:	pullnews.pod		; $(POD2MAN) -s 1 $? > $@
../man/rnews.1:		rnews.pod		; $(POD2MAN) -s 1 $? > $@
../man/shrinkfile.1:	shrinkfile.pod		; $(POD2MAN) -s 1 $? > $@
../man/simpleftp.1:	simpleftp.pod		; $(POD2MAN) -s 1 $? > $@

../man/libinn.3:	libinn.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinnauth.3:	libinnauth.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinnhist.3:	libinnhist.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinnstorage.3:	libinnstorage.pod	; $(POD2MAN) -s 3 $? > $@
../man/libinn_clientlib.3: libinn_clientlib.pod	; $(POD2MAN) -s 3 $? > $@
../man/libinn_dbz.3:	libinn_dbz.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinn_inndcomm.3: libinn_inndcomm.pod	; $(POD2MAN) -s 3 $? > $@
../man/libinn_list.3:	libinn_list.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinn_qio.3:	libinn_qio.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinn_tst.3:	libinn_tst.pod		; $(POD2MAN) -s 3 $? > $@
../man/libinn_uwildmat.3: libinn_uwildmat.pod	; $(POD2MAN) -s 3 $? > $@

../man/active.5:	active.pod		; $(POD2MAN) -s 5 $? > $@
../man/active.times.5:	active.times.pod	; $(POD2MAN) -s 5 $? > $@
../man/buffindexed.conf.5: buffindexed.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/control.ctl.5:	control.ctl.pod		; $(POD2MAN) -s 5 $? > $@
../man/cycbuff.conf.5:	cycbuff.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/distrib.pats.5:	distrib.pats.pod	; $(POD2MAN) -s 5 $? > $@
../man/distributions.5:	distributions.pod	; $(POD2MAN) -s 5 $? > $@
../man/expire.ctl.5:	expire.ctl.pod		; $(POD2MAN) -s 5 $? > $@
../man/history.5:	history.pod		; $(POD2MAN) -s 5 $? > $@
../man/incoming.conf.5:	incoming.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/inn.conf.5:	inn.conf.pod		; $(POD2MAN) -s 5 $? > $@
../man/innfeed.conf.5:	innfeed.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/innreport.conf.5: innreport.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/inn-secrets.conf.5: inn-secrets.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/innwatch.ctl.5:	innwatch.ctl.pod	; $(POD2MAN) -s 5 $? > $@
../man/moderators.5:	moderators.pod		; $(POD2MAN) -s 5 $? > $@
../man/motd.news.5:	motd.news.pod		; $(POD2MAN) -s 5 $? > $@
../man/newsfeeds.5:	newsfeeds.pod		; $(POD2MAN) -s 5 $? > $@
../man/newsgroups.5:	newsgroups.pod		; $(POD2MAN) -s 5 $? > $@
../man/newslog.5:	newslog.pod		; $(POD2MAN) -s 5 $? > $@
../man/nnrpd.track.5:	nnrpd.track.pod		; $(POD2MAN) -s 5 $? > $@
../man/nntpsend.ctl.5:	nntpsend.ctl.pod	; $(POD2MAN) -s 5 $? > $@
../man/ovdb.5:		ovdb.pod		; $(POD2MAN) -s 5 $? > $@
../man/ovsqlite.5:	ovsqlite.pod		; $(POD2MAN) -s 5 $? > $@
../man/passwd.nntp.5:	passwd.nntp.pod		; $(POD2MAN) -s 5 $? > $@
../man/inn-radius.conf.5: inn-radius.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/readers.conf.5:	readers.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/storage.conf.5:	storage.conf.pod	; $(POD2MAN) -s 5 $? > $@
../man/subscriptions.5:	subscriptions.pod	; $(POD2MAN) -s 5 $? > $@

../man/actsync.8:	actsync.pod		; $(POD2MAN) -s 8 $? > $@
../man/archive.8:	archive.pod		; $(POD2MAN) -s 8 $? > $@
../man/auth_krb5.8:	auth_krb5.pod		; $(POD2MAN) -s 8 $? > $@
../man/batcher.8:	batcher.pod		; $(POD2MAN) -s 8 $? > $@
../man/buffchan.8:	buffchan.pod		; $(POD2MAN) -s 8 $? > $@
../man/ckpasswd.8:	ckpasswd.pod		; $(POD2MAN) -s 8 $? > $@
../man/cnfsheadconf.8:	cnfsheadconf.pod	; $(POD2MAN) -s 8 $? > $@
../man/cnfsstat.8:	cnfsstat.pod		; $(POD2MAN) -s 8 $? > $@
../man/controlchan.8:	controlchan.pod		; $(POD2MAN) -s 8 $? > $@
../man/ctlinnd.8:	ctlinnd.pod		; $(POD2MAN) -s 8 $? > $@
../man/cvtbatch.8:	cvtbatch.pod		; $(POD2MAN) -s 8 $? > $@
../man/docheckgroups.8:	docheckgroups.pod	; $(POD2MAN) -s 8 $? > $@
../man/domain.8:	domain.pod		; $(POD2MAN) -s 8 $? > $@
../man/expire.8:	expire.pod		; $(POD2MAN) -s 8 $? > $@
../man/expireover.8:	expireover.pod		; $(POD2MAN) -s 8 $? > $@
../man/expirerm.8:	expirerm.pod		; $(POD2MAN) -s 8 $? > $@
../man/ident.8:		ident.pod		; $(POD2MAN) -s 8 $? > $@
../man/innbind.8:	innbind.pod		; $(POD2MAN) -s 8 $? > $@
../man/inncheck.8:	inncheck.pod		; $(POD2MAN) -s 8 $? > $@
../man/innd.8:		innd.pod		; $(POD2MAN) -s 8 $? > $@
../man/inndf.8:		inndf.pod		; $(POD2MAN) -s 8 $? > $@
../man/innfeed.8:	innfeed.pod		; $(POD2MAN) -s 8 $? > $@
../man/innreport.8:	innreport.pod		; $(POD2MAN) -s 8 $? > $@
../man/innstat.8:	innstat.pod		; $(POD2MAN) -s 8 $? > $@
../man/innupgrade.8:	innupgrade.pod		; $(POD2MAN) -s 8 $? > $@
../man/innwatch.8:	innwatch.pod		; $(POD2MAN) -s 8 $? > $@
../man/innxbatch.8:	innxbatch.pod		; $(POD2MAN) -s 8 $? > $@
../man/innxmit.8:	innxmit.pod		; $(POD2MAN) -s 8 $? > $@
../man/makedbz.8:	makedbz.pod		; $(POD2MAN) -s 8 $? > $@
../man/makehistory.8:	makehistory.pod		; $(POD2MAN) -s 8 $? > $@
../man/mod-active.8:	mod-active.pod		; $(POD2MAN) -s 8 $? > $@
../man/news.daily.8:	news.daily.pod		; $(POD2MAN) -s 8 $? > $@
../man/news2mail.8:	news2mail.pod		; $(POD2MAN) -s 8 $? > $@
../man/ninpaths.8:	ninpaths.pod		; $(POD2MAN) -s 8 $? > $@
../man/nnrpd.8:		nnrpd.pod		; $(POD2MAN) -s 8 $? > $@
../man/nntpsend.8:	nntpsend.pod		; $(POD2MAN) -s 8 $? > $@
../man/ovdb_init.8:	ovdb_init.pod		; $(POD2MAN) -s 8 $? > $@
../man/ovdb_monitor.8:	ovdb_monitor.pod	; $(POD2MAN) -s 8 $? > $@
../man/ovdb_server.8:	ovdb_server.pod		; $(POD2MAN) -s 8 $? > $@
../man/ovdb_stat.8:	ovdb_stat.pod		; $(POD2MAN) -s 8 $? > $@
../man/overchan.8:	overchan.pod		; $(POD2MAN) -s 8 $? > $@
../man/ovsqlite-server.8: ovsqlite-server.pod	; $(POD2MAN) -s 8 $? > $@
../man/ovsqlite-util.8: ovsqlite-util.pod	; $(POD2MAN) -s 8 $? > $@
../man/procbatch.8:	procbatch.pod		; $(POD2MAN) -s 8 $? > $@
../man/prunehistory.8:	prunehistory.pod	; $(POD2MAN) -s 8 $? > $@
../man/radius.8:	radius.pod		; $(POD2MAN) -s 8 $? > $@
../man/rc.news.8:	rc.news.pod		; $(POD2MAN) -s 8 $? > $@
../man/scanlogs.8:	scanlogs.pod		; $(POD2MAN) -s 8 $? > $@
../man/scanspool.8:	scanspool.pod		; $(POD2MAN) -s 8 $? > $@
../man/send-ihave.8:	send-ihave.pod		; $(POD2MAN) -s 8 $? > $@
../man/sendinpaths.8:	sendinpaths.pod		; $(POD2MAN) -s 8 $? > $@
../man/shlock.8:	shlock.pod		; $(POD2MAN) -s 8 $? > $@
../man/sm.8:		sm.pod			; $(POD2MAN) -s 8 $? > $@
../man/tally.control.8:	tally.control.pod	; $(POD2MAN) -s 8 $? > $@
../man/tdx-util.8:	tdx-util.pod		; $(POD2MAN) -s 8 $? > $@
../man/tinyleaf.8:	tinyleaf.pod		; $(POD2MAN) -s 8 $? > $@
../man/writelog.8:	writelog.pod		; $(POD2MAN) -s 8 $? > $@
