# -*- sh -*-

#This is a UNIX-only makefile.  For other systems, get a makefile from
#src/mkfiles/

# If you want to change these variables, re-run the configure script.
INSTALL= /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
prefix = /usr/local
exec_prefix = ${prefix}
libdir = ${exec_prefix}/lib
pkgconfigdir = ${libdir}/pkgconfig
#---------------------------------------------------------------------------
# DESTDIR is designed to facilitate making packages.  Normally it is empty
#---------------------------------------------------------------------------
#DESTDIR =
DEST_PKGCONFIGDIR = $(DESTDIR)$(pkgconfigdir)
#
MKINSDIR = autoconf/mkinsdir.sh


SHELL = /bin/sh

all: elf
Makefile: configure autoconf/Makefile.in
	@echo "Makefile is older than the configure script".
	@echo "Please re-run the configure script."
	@exit 1
slsh/Makefile: configure slsh/Makefile.in
	@echo "slsh/Makefile is older than its dependencies".
	@echo "Please re-run the configure script."
	@exit 1
modules/Makefile: configure modules/Makefile.in
	@echo "modules/Makefile is older than its dependencies".
	@echo "Please re-run the configure script."
	@exit 1
src/Makefile: configure src/Makefile.in src/config.hin
	@echo "src/Makefile is older than its dependencies".
	@echo "Please re-run the configure script."
	@exit 1
#
makefiles: Makefile slsh/Makefile modules/Makefile src/Makefile
help:
	@echo "make install : install a shared version of the library"
	@echo "make install-static : install a static version"
	@echo "make install-all : install both shared and static versions"
	@echo "make check : Build the library and run the regression tests"
slang.pc: configure autoconf/slangpc.in
	@echo "slang.pc needs to be updated -- rerun configure"
	@exit 1
static: makefiles slang.pc
	cd src; $(MAKE) static
	cd slsh; $(MAKE) all
elf: makefiles slang.pc
	cd src; $(MAKE) elf
	cd slsh; $(MAKE) all
	cd modules; $(MAKE) all
	@echo Use make install to install it.
runtests:
	cd src; $(MAKE) static
	cd src; $(MAKE) runtests
check: runtests

demos:
	cd demo; $(MAKE)
clean:
	/bin/rm -f *~
	cd src; $(MAKE) clean
	cd modules; $(MAKE) clean
	cd slsh; $(MAKE) clean
	cd demo; $(MAKE) clean
install-static:
	cd src; $(MAKE) install-static
install-pkgconfig: slang.pc
	$(MKINSDIR) $(DEST_PKGCONFIGDIR)
	$(INSTALL_DATA) slang.pc $(DEST_PKGCONFIGDIR)/
install-elf:
	cd src; $(MAKE) install-elf
	@echo Now installing slsh
	cd slsh; $(MAKE) install
	@echo Now installing the modules
	cd modules; $(MAKE) install
	@echo ""
	@echo "On some systems, e.g., linux, you may also have to run ldconfig."
	@echo ""
install: install-elf install-pkgconfig
install-all: install-elf install-static install-pkgconfig
install-links:
	cd src; $(MAKE) install-links
#
distclean:
	/bin/rm -f *~ Makefile config.status config.log config.cache files.pck slang.pc
	cd src; $(MAKE) distclean
	cd demo; $(MAKE) distclean
	cd modules; $(MAKE) distclean
	cd slsh; $(MAKE) distclean
#
.PHONY: all help static elf install clean check install-elf install-static makefiles install-pkgconfig
#
