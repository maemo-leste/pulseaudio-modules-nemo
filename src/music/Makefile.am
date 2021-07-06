AM_LIBADD =
AM_CFLAGS =						\
	$(PULSEAUDIO_CFLAGS)				\
	-I$(top_srcdir)/src/music			\
	-I$(top_srcdir)/src/common/include/meego


modlibexec_LTLIBRARIES = module-meego-music.la

libmeegocommoninclude_HEADERS = module-music-api.h
libmeegocommonincludedir = $(includedir)/pulsecore/modules/meego

###################################
#              EAP                #
###################################
noinst_HEADERS = module-meego-music-symdef.h

module_meego_music_la_SOURCES = module-meego-music.c

module_meego_music_la_LDFLAGS = -module -avoid-version -Wl,-no-undefined -Wl,-z,noexecstack
module_meego_music_la_LIBADD = -lm $(top_builddir)/src/common/libmeego-common.la $(AM_LIBADD) $(PULSEAUDIO_LIBS)
module_meego_music_la_CFLAGS = $(AM_CFLAGS)
