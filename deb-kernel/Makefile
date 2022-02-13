DESTDIR ?=
PREFIX ?= /usr/local
BINDIR ?= $(PREFIX)/bin

all:
	@ echo "Use: make install, make uninstall"

install:
	install -p -d $(DESTDIR)$(BINDIR)
	install -p -m0755 build-kernel $(DESTDIR)$(BINDIR)/build-kernel
	install -p -m0755 install-kernel $(DESTDIR)$(BINDIR)/install-kernel

uninstall:
	rm -fv $(DESTDIR)$(BINDIR)/build-kernel
	rm -fv $(DESTDIR)$(BINDIR)/install-kernel
