include ../../Makefile.global

top	= ../..

SEC1	= convdate.1 fastrm.1 gencancel.1 getlist.1 \
	grephistory.1 inews.1 \
	innconfval.1 innmail.1 nntpget.1 pgpverify.1 pullnews.1 rnews.1 \
	shrinkfile.1 simpleftp.1

SEC3	= libinn.3 libinn_clientlib.3 libinn_dbz.3 libinn_inndcomm.3 \
	libinn_list.3 libinn_qio.3 libinn_tst.3 libinn_uwildmat.3 \
	libinnauth.3 libinnhist.3 libinnstorage.3

SEC3PM	= INN__Config.3pm \
	INN__Utils__Shlock.3pm INN__ovsqlite_client.3pm

SEC5	= active.5 active.times.5 buffindexed.conf.5 control.ctl.5 \
	cycbuff.conf.5 distrib.pats.5 distributions.5 expire.ctl.5 \
	history.5 incoming.conf.5 \
	inn.conf.5 innfeed.conf.5 innreport.conf.5 inn-secrets.conf.5 \
	innwatch.ctl.5 moderators.5 motd.news.5 \
	newsfeeds.5 newsgroups.5 newslog.5 nnrpd.track.5 nntpsend.ctl.5 ovdb.5 \
	ovsqlite.5 passwd.nntp.5 inn-radius.conf.5 readers.conf.5 \
	storage.conf.5 subscriptions.5

SEC8	= actsync.8 archive.8 batcher.8 buffchan.8 ckpasswd.8 \
	cnfsheadconf.8 cnfsstat.8 controlchan.8 ctlinnd.8 cvtbatch.8 \
	delayer.8 docheckgroups.8 domain.8 expire.8 expireover.8 expirerm.8 \
	ident.8 \
	innbind.8 inncheck.8 innd.8 inndf.8 innfeed.8 innreport.8 innstat.8 \
	innupgrade.8 innwatch.8 innxbatch.8 innxmit.8 mailpost.8 makedbz.8 \
	makehistory.8 mod-active.8 news.daily.8 news2mail.8 ninpaths.8 \
	nnrpd.8 nntpsend.8 ovdb_init.8 ovdb_monitor.8 ovdb_server.8 \
	ovdb_stat.8 overchan.8 ovsqlite-server.8 ovsqlite-util.8 perl-nocem.8 \
	procbatch.8 prunehistory.8 radius.8 rc.news.8 \
	scanlogs.8 scanspool.8 send-ihave.8 send-uucp.8 sendinpaths.8 shlock.8 \
	sm.8 tally.control.8 tdx-util.8 tinyleaf.8 writelog.8

all:
clobber clean distclean:
profiled:

install: install-man1 install-man3 install-man3pm install-man5 install-man8

install-man1:
	for M in $(SEC1) ; do \
	    $(CP_MAN) $$M $D$(MAN1)/$$M ; \
	done

install-man3:
	for M in $(SEC3) ; do \
	    $(CP_MAN) $$M $D$(MAN3)/$$M ; \
	done

install-man3pm:
	$(CP_MAN) INN__Config.3pm $D$(MAN3PM)/INN\:\:Config.$(MAN3PM_EXT)
	$(CP_MAN) INN__Utils__Shlock.3pm $D$(MAN3PM)/INN\:\:Utils\:\:Shlock.$(MAN3PM_EXT)
	$(CP_MAN) INN__ovsqlite_client.3pm $D$(MAN3PM)/INN\:\:ovsqlite_client.$(MAN3PM_EXT)

# We also create symbolic links between config files and programs.
# We try to use relative symbolic links, when possible.  As '-ef' is
# not required by POSIX, we make absolute symbolic links before this
# test, in case it fails.
install-man5:
	for M in $(SEC5) ; do \
	    $(CP_MAN) $$M $D$(MAN5)/$$M ; \
	done
	rm -f $D$(MAN5)/motd.innd.5 $D$(MAN5)/motd.nnrpd.5
	$(LN_S) motd.news.5 $D$(MAN5)/motd.innd.5
	$(LN_S) motd.news.5 $D$(MAN5)/motd.nnrpd.5
	rm -f $D$(MAN5)/localgroups.5 $D$(MAN5)/nocem.ctl.5
	$(LN_S) $(MAN8)/docheckgroups.8 $D$(MAN5)/localgroups.5
	$(LN_S) $(MAN8)/perl-nocem.8 $D$(MAN5)/nocem.ctl.5
	if [ $D$(MAN5)/../man8 -ef $D$(MAN8) ] ; then \
	    rm -f $D$(MAN5)/localgroups.5 $D$(MAN5)/nocem.ctl.5 ; \
	    $(LN_S) ../man8/docheckgroups.8 $D$(MAN5)/localgroups.5 ; \
	    $(LN_S) ../man8/perl-nocem.8 $D$(MAN5)/nocem.ctl.5 ; \
	fi

# auth_krb5 is conditionally compiled, so handle it specially.  actsync(8)
# also covers actsyncd.
install-man8:
	for M in $(SEC8) ; do \
	    $(CP_MAN) $$M $D$(MAN8)/$$M ; \
	done
	rm -f $D$(MAN8)/actsyncd.8
	$(LN_S) actsync.8 $D$(MAN8)/actsyncd.8
	rm -f $D$(MAN8)/imapfeed.8
	$(LN_S) innfeed.8 $D$(MAN8)/imapfeed.8
	rm -f $D$(MAN8)/inpaths.8
	$(LN_S) ninpaths.8 $D$(MAN8)/inpaths.8
	rm -f $D$(MAN8)/sendxbatches.8
	$(LN_S) innxbatch.8 $D$(MAN8)/sendxbatches.8
	if [ x"$(KRB5_AUTH)" != x ] ; then \
	    $(CP_MAN) auth_krb5.8 $D$(MAN8)/auth_krb5.8 ; \
	fi
