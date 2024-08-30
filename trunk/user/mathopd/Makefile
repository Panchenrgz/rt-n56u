SRC_NAME = mathopd-1.5p8
THISDIR = $(shell pwd)
FLAGS := DEFS=""
CFLAGS := -O3
LDFLAGS :=

all: extract
	$(MAKE) -j$(HOST_NCPU) -C $(SRC_NAME)/src

extract:
	( if [ ! -d $(SRC_NAME) ]; then \
		tar xf $(SRC_NAME).tar.gz ; \
		patch $(SRC_NAME)/src/Makefile < mathopdAddCFLAG.patch ; \
	fi )

clean:
	if [ -f $(SRC_NAME)/src/Makefile ] ; then \
		$(MAKE) -C $(SRC_NAME)/src clean ; \
	fi

romfs:
	$(ROMFSINST) $(THISDIR)/$(SRC_NAME)/src/mathopd /usr/bin/mathopd
	$(ROMFSINST) $(THISDIR)/mathopd.conf /etc/mathopd.conf
