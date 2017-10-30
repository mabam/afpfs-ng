bin_PROGRAMS = afpfsd mount_afp2

mount_afp2_SOURCES = client.c
mount_afp2_CFLAGS = -I$(top_srcdir)/include -D_FILE_OFFSET_BITS=64 @CFLAGS@
mount_afp2_LDADD = $(top_builddir)/lib/libafpclient.la

afpfsd_SOURCES = commands.c daemon.c fuse_int.c fuse_error.c
afpfsd_LDADD = $(top_builddir)/lib/libafpclient.la /usr/local/lib/libosxfuse.la
afpfsd_LDFLAGS = -export-dynamic /usr/local/lib/libosxfuse.la
afpfsd_CFLAGS = -I$(top_srcdir)/include -D_FILE_OFFSET_BITS=64 @CFLAGS@

install-data-hook:
	mkdir -p $(DESTDIR)/$(mandir)/man1
	cp mount_afp2.1 $(DESTDIR)/$(mandir)/man1
	cp afpfsd.1 $(DESTDIR)/$(mandir)/man1
	cp afp_client.1 $(DESTDIR)/$(mandir)/man1

install-exec-hook:
	rm -f $(DESTDIR)$(bindir)/afp_client
	$(LN_S) mount_afp2 $(DESTDIR)$(bindir)/afp_client
	cp afpfs $(DESTDIR)$(bindir)/afpfs
