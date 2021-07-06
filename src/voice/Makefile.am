AM_CFLAGS =						\
	$(PULSEAUDIO_CFLAGS)				\
	-I$(top_srcdir)/src/voice			\
	-I$(top_srcdir)/src/common/include/meego

AM_LIBADD =							\
	$(top_builddir)/src/common/libmeego-common.la		\
	$(PULSEAUDIO_LIBS)

###################################
#             Voice               #
###################################
noinst_HEADERS = module-meego-voice-symdef.h

modlibexec_LTLIBRARIES = module-meego-voice.la

libmeegocommoninclude_HEADERS = module-voice-api.h
libmeegocommonincludedir = $(includedir)/pulsecore/modules/meego

module_meego_voice_la_SOURCES =			\
	module-meego-voice.c			\
	voice-mainloop-handler.c		\
	voice-aep-sink-input.c			\
	voice-hw-sink-input.c			\
	voice-hw-source-output.c		\
	voice-raw-sink.c			\
	voice-raw-source.c			\
	voice-util.c				\
	voice-voip-sink.c			\
	voice-voip-source.c

if X86
module_meego_voice_la_LDFLAGS = -module -avoid-version -lm -Wl,-z,noexecstack
else
module_meego_voice_la_LDFLAGS = -module -avoid-version -lm -Wl,-no-undefined -Wl,-z,noexecstack
endif
module_meego_voice_la_LIBADD = $(AM_LIBADD)
module_meego_voice_la_CFLAGS = $(AM_CFLAGS)
