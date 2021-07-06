AM_LIBADD =
AM_CFLAGS =						\
	$(PULSEAUDIO_CFLAGS)				\
	-I$(top_srcdir)/src/record			\
	-I$(top_srcdir)/src/common/include/meego

AM_LIBADD += $(top_builddir)/src/common/libmeego-common.la

modlibexec_LTLIBRARIES = module-meego-record.la

libmeegocommoninclude_HEADERS = module-record-api.h
libmeegocommonincludedir = $(includedir)/pulsecore/modules/meego

noinst_HEADERS = module-meego-record-symdef.h

module_meego_record_la_SOURCES = module-meego-record.c

module_meego_record_la_LDFLAGS = -module -avoid-version -Wl,-no-undefined -Wl,-z,noexecstack
module_meego_record_la_LIBADD = $(AM_LIBADD) $(PULSEAUDIO_LIBS) -lm
module_meego_record_la_CFLAGS = $(AM_CFLAGS)
