PKGDIR		?= ../..
L4DIR		?= $(PKGDIR)/../..

TARGET		= libzstd.a libzstd.so
SYSTEMS	        = $(SYSTEMS_PLAIN)
CONTRIBDIR      = $(SRC_DIR)/../contrib/lib
CONTRIB_INCDIR  = zstd
PRIVATE_INCDIR  = $(CONTRIBDIR) $(CONTRIBDIR)/common
DEFINES         = -DXXH_NAMESPACE=ZSTD_

vpath %.c $(CONTRIBDIR)
vpath %.S $(CONTRIBDIR)

# see libzstd.mk
ZSTD_COMMON_FILES      := $(sort $(wildcard $(CONTRIBDIR)/common/*.c))
ZSTD_COMPRESS_FILES    := $(sort $(wildcard $(CONTRIBDIR)/compress/*.c))
ZSTD_DECOMPRESS_FILES  := $(sort $(wildcard $(CONTRIBDIR)/decompress/*.c))
ZSTD_DICTBUILDER_FILES := $(sort $(wildcard $(CONTRIBDIR)/dictBuilder/*.c))
ZSTD_DEPRECATED_FILES  := $(sort $(wildcard $(CONTRIBDIR)/deprecated/*.c))

ZSTD_DECOMPRESS_AMD64_ASM_FILES := $(sort $(wildcard $(CONTRIBDIR)/decompress/*_amd64.S))

# selection to use
ZSTD_FILES := $(ZSTD_COMMON_FILES)
ZSTD_FILES += $(ZSTD_COMPRESS_FILES)
ZSTD_FILES += $(ZSTD_DECOMPRESS_FILES)
#ZSTD_FILES += $(ZSTD_DICTBUILDER_FILES)
#ZSTD_FILES += $(ZSTD_DEPRECATED_FILES)

SRC_C        = $(patsubst $(CONTRIBDIR)/%,%,$(ZSTD_FILES))
SRC_S_amd64 += $(patsubst $(CONTRIBDIR)/%,%,$(ZSTD_DECOMPRESS_AMD64_ASM_FILES))

include $(L4DIR)/mk/lib.mk
