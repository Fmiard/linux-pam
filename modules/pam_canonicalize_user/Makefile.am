CLEANFILES = *~
MAINTAINERCLEANFILES = $(MANS) README

EXTRA_DIST = $(XMLS)

if HAVE_DOC
dist_man_MANS = pam_canonicalize_user.8
endif
XMLS = README.xml pam_canonicalize_user.8.xml
dist_check_SCRIPTS = tst-pam_canonicalize_user
TESTS = $(dist_check_SCRIPTS)

securelibdir = $(SECUREDIR)
if HAVE_VENDORDIR
secureconfdir = $(VENDOR_SCONFIGDIR)
else
secureconfdir = $(SCONFIGDIR)
endif

AM_CFLAGS = -I$(top_srcdir)/libpam/include -I$(top_srcdir)/libpamc/include \
	    $(WARN_CFLAGS)
AM_LDFLAGS = -no-undefined -avoid-version -module
if HAVE_VERSIONING
  AM_LDFLAGS += -Wl,--version-script=$(srcdir)/../modules.map
endif

securelib_LTLIBRARIES = pam_canonicalize_user.la
pam_canonicalize_user_la_LIBADD = $(top_builddir)/libpam/libpam.la

check_PROGRAMS = tst-pam_canonicalize_user-retval
tst_pam_canonicalize_user_retval_LDADD = $(top_builddir)/libpam/libpam.la

if ENABLE_REGENERATE_MAN
dist_noinst_DATA = README
-include $(top_srcdir)/Make.xml.rules
endif
