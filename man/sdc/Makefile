#
# Copyright 2019 Joyent, Inc.
#

ROOT=$(PWD)
RONNJS=/opt/local/bin/node $(ROOT)/../../tools/ronnjs/bin/ronn.js

DESTDIR =		../../proto

CLEANFILES =		sdc-factoryreset.1

SDCMAN1_PAGES =					\
			sdc-factoryreset	\
			sdc-lastcomm		\
			sdc-zfs-io-throttle

SDCMAN1_FILES =		$(SDCMAN1_PAGES:%=%.1)

PROTO_SDCMAN1_DIR =	$(DESTDIR)/smartdc/man/man1
PROTO_SDCMAN1_FILES =	$(SDCMAN1_FILES:%=$(PROTO_SDCMAN1_DIR)/%)

MAN1_PAGES =					\
			json

MAN1_FILES =		$(MAN1_PAGES:%=%.1)

PROTO_MAN1_DIR =	$(DESTDIR)/share/man/man1
PROTO_MAN1_FILES =	$(MAN1_FILES:%=$(PROTO_MAN1_DIR)/%)

MAN1M_PAGES =					\
			fssstat

MAN1M_FILES =		$(MAN1M_PAGES:%=%.1)

PROTO_MAN1M_DIR =	$(DESTDIR)/usr/share/man/man1m
PROTO_MAN1_FILES =	$(MAN1_FILES:%=$(PROTO_MAN1_DIR)/%)

all: $(SDCMAN1_FILES) $(MAN1_FILES) $(MAN1M_FILES)

install: $(PROTO_SDCMAN1_FILES) $(PROTO_MAN1_FILES) $(PROTO_MAN1M_FILES)

$(PROTO_SDCMAN1_DIR)/%: %
	mkdir -p $(@D)
	rm -f $@
	cp $< $@
	touch $@

$(PROTO_MAN1_DIR)/%: %
	mkdir -p $(@D)
	rm -f $@
	cp $< $@
	touch $@

$(PROTO_MAN1M_DIR)/%: %
	mkdir -p $(@D)
	rm -f $@
	cp $< $@
	touch $@

%: %.md
	rm -f $@
	$(RONNJS) --roff $< > $@

clean:
	rm -f $(CLEANFILES)
