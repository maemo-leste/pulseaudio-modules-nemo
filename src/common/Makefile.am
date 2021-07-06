AM_CFLAGS = \
	-I$(top_srcdir)/src/common \
	-I$(top_srcdir)/src/common/include \
	-I$(top_srcdir)/src/common/include/meego \
	$(PULSEAUDIO_CFLAGS)

modlibexec_LTLIBRARIES = libmeego-common.la

libmeego_common_la_SOURCES = \
	optimized.c include/meego/optimized.h \
	pa-optimized.c include/meego/pa-optimized.h \
	memory.c include/meego/memory.h \
	parameter-hook.c \
	include/meego/parameter-hook.h \
	include/meego/parameter-hook-implementor.h \
	include/meego/parameter-modifier.h \
	algorithm-hook.c include/meego/algorithm-hook.h \
	algorithm-base.c include/meego/algorithm-base.h \
	include/meego/proplist-meego.h \
	call-state-tracker.c include/meego/call-state-tracher.h \
	volume-proxy.c include/meego/volume-proxy.h \
	shared-data.c include/meego/shared-data.h

libmeego_common_la_LDFLAGS = -avoid-version
libmeego_common_la_LIBADD = $(PULSEAUDIO_LIBS)
libmeego_common_la_CFLAGS = $(AM_CFLAGS)

if X86
libmeego_common_la_SOURCES += \
	src-8-to-48.c \
	src-48-to-8.c \
	src-16-to-48.c \
	src-48-to-16.c
else
libmeego_common_la_LIBADD += \
	src-8-to-48-neon.o \
	src-48-to-8-neon.o \
	src-16-to-48-neon.o \
	src-48-to-16-neon.o
if ARM_HARDFP
%-neon.o: speech_src_neon_hardfp.a
	ar x speech_src_neon_hardfp.a
else
%-neon.o: speech_src_neon.a
	ar x speech_src_neon.a
endif
endif

libmeegocommoninclude_HEADERS = include/meego/algorithm-base.h \
	include/meego/algorithm-hook.h \
	include/meego/call-state-tracker.h \
	include/meego/memory.h \
	include/meego/optimized.h \
	include/meego/pa-optimized.h \
	include/meego/parameter-hook.h \
	include/meego/parameter-hook-implementor.h \
	include/meego/parameter-modifier.h \
	include/meego/proplist-meego.h \
	include/meego/proplist-nemo.h \
	include/meego/shared-data.h \
	include/meego/src-16-to-48.h \
	include/meego/src-48-to-16.h \
	include/meego/src-48-to-8.h \
	include/meego/src-8-to-48.h \
	include/meego/volume-proxy.h

libmeegocommonincludedir = $(includedir)/pulsecore/modules/meego

libmeegocommonincludesf_HEADERS = include/sailfishos/defines.h
libmeegocommonincludesfdir = $(includedir)/pulsecore/modules/sailfishos

TESTS = check_common
check_PROGRAMS = check_common
check_common_SOURCES = tests.c
check_common_LDADD = libmeego-common.la $(CHECK_LIBS) $(PULSEAUDIO_LIBS)
check_common_CFLAGS = $(AM_CFLAGS) $(CHECK_CFLAGS)

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA  = libmeego-common.pc
