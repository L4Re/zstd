PKGDIR		?= ../..
L4DIR		?= $(PKGDIR)/../..

TARGET		= libzstd.a libzstd.so
SYSTEMS	        = $(SYSTEMS_PLAIN)
CONTRIBDIR      = $(SRC_DIR)/../contrib/lib
CONTRIB_INCDIR  = zstd
PRIVATE_INCDIR  = $(CONTRIBDIR) $(CONTRIBDIR)/common
DEFINES         = -DXXH_NAMESPACE=ZSTD_

vpath %.c $(CONTRIBDIR)

ZSTDCOMMON_FILES := $(sort $(wildcard $(CONTRIBDIR)/common/*.c))
ZSTDCOMP_FILES   := $(sort $(wildcard $(CONTRIBDIR)/compress/*.c))
ZSTDDECOMP_FILES := $(sort $(wildcard $(CONTRIBDIR)/decompress/*.c))
ZDICT_FILES      := $(sort $(wildcard $(CONTRIBDIR)/dictBuilder/*.c))
ZDEPR_FILES      := $(sort $(wildcard $(CONTRIBDIR)/deprecated/*.c))

# selection to use
ZSTD_FILES := $(ZSTDCOMMON_FILES)
ZSTD_FILES += $(ZSTDCOMP_FILES)
ZSTD_FILES += $(ZSTDDECOMP_FILES)
#ZSTD_FILES += $(ZDICT_FILES)
#ZSTD_FILES += $(ZDEPR_FILES)

SRC_C       = $(patsubst $(CONTRIBDIR)/%,%,$(ZSTD_FILES))

include $(L4DIR)/mk/lib.mk
