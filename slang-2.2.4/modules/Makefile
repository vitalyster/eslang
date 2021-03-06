# -*- sh -*-
MODULES = slsmg-module.so termios-module.so select-module.so fcntl-module.so \
  varray-module.so socket-module.so rand-module.so fork-module.so \
  csv-module.so   \
  iconv-module.so   sysconf-module.so
SLFILES = slsmg termios select fcntl varray socket pcre png iconv \
  onig rand csv zlib fork sysconf
#---------------------------------------------------------------------------
CC		= gcc
CFLAGS		= -g -O2 -fPIC  
LDFLAGS		= 
CC_SHARED 	= $(CC) $(CFLAGS) -shared -fPIC
CONFIG_DIR	= /home/maxim/synrc/pie/deps/eslang/slang-2.2.4
SRCDIR		= $(CONFIG_DIR)/modules
OBJDIR		= $(ARCH)objs
ELFDIR          = /home/maxim/synrc/pie/deps/eslang/slang-2.2.4/src/$(ARCH)elfobjs
#---------------------------------------------------------------------------
# Installation location of the slang library
#---------------------------------------------------------------------------
prefix 		= /usr/local
exec_prefix 	= ${prefix}
SLANG_SRCINC	= -I/home/maxim/synrc/pie/deps/eslang/slang-2.2.4/src
DLL_IMPLIB_NAME = 
# On some systems, the module must be linked to the slang library,
# but not all do.  If you have such system, point SLANG_LIB to the
# slang library, otherwise leave it blank.
SLANG_LIB	= 

#---------------------------------------------------------------------------
# If building the PCRE module, you may need to set these
#---------------------------------------------------------------------------
PCRE_INC	= 
PCRE_LIB	=  -lpcre
#---------------------------------------------------------------------------
# If building the PNG module, you may need to set these
#---------------------------------------------------------------------------
PNG_INC	= 
PNG_LIB	=  -lpng
#---------------------------------------------------------------------------
# If building the ICONV module, you may need to set these
#---------------------------------------------------------------------------
ICONV_INC	= 
ICONV_LIB	= 
#---------------------------------------------------------------------------
# If building the ONIG module, you may need to set these
#---------------------------------------------------------------------------
ONIG_INC	= 
ONIG_LIB	=  -lonig
#---------------------------------------------------------------------------
# If building the ZLIB module, you may need to set these
#---------------------------------------------------------------------------
ZLIB_INC	= 
ZLIB_LIB	=  -lz
#---------------------------------------------------------------------------
# If building the SOCKET module, you may need to set these
#---------------------------------------------------------------------------
SOCKET_LIBS = 
#---------------------------------------------------------------------------
# Installation location of the modules
#---------------------------------------------------------------------------
MODULE_INSTALL_DIR = ${exec_prefix}/lib/slang/v2/modules
INSTALL		= /usr/bin/install -c
INSTALL_DATA	= ${INSTALL} -m 644
INSTALL_MODULE	= $(INSTALL_DATA)
MKINSDIR	= $(CONFIG_DIR)/autoconf/mkinsdir.sh
SLSH_DIR	= $(prefix)/share/slsh
CMAPS_DIR	= $(SLSH_DIR)/cmaps
HELP_DIR	= $(SLSH_DIR)/help
#---------------------------------------------------------------------------
# DESTDIR is designed to facilitate making packages.  Normally it is empty
#---------------------------------------------------------------------------
#DESTDIR =
DEST_MODULEDIR	= $(DESTDIR)$(MODULE_INSTALL_DIR)
DEST_SLSH_DIR	= $(DESTDIR)$(SLSH_DIR)
DEST_CMAPSDIR	= $(DESTDIR)$(CMAPS_DIR)
DEST_HELPDIR	= $(DESTDIR)$(HELP_DIR)
#---------------------------------------------------------------------------
RPATH = -Wl,-R${exec_prefix}/lib

LIBS = $(LDFLAGS) $(RPATH) $(SLANG_LIB) $(DL_LIB) -lm
INCS = $(SLANG_SRCINC)
#---------------------------------------------------------------------------
all: $(MODULES)

config.h: ../src/config.h
	cp ../src/config.h .
$(OBJDIR):
	-$(MKINSDIR) $(OBJDIR)
#
slsmg-module.so: $(OBJDIR) $(OBJDIR)/slsmg-module.so
$(OBJDIR)/slsmg-module.so: slsmg-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/slsmg-module.c -o slsmg-module.so $(LIBS)
rand-module.so: $(OBJDIR) $(OBJDIR)/rand-module.so
$(OBJDIR)/rand-module.so: rand-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/rand-module.c -o rand-module.so $(LIBS)
newt-module.so: $(OBJDIR) $(OBJDIR)/newt-module.so
$(OBJDIR)/newt-module.so: newt-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/newt-module.c -o newt-module.so -lnewt $(LIBS)
termios-module.so: $(OBJDIR) $(OBJDIR)/termios-module.so
$(OBJDIR)/termios-module.so: termios-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/termios-module.c -o termios-module.so $(LIBS)
select-module.so: $(OBJDIR) $(OBJDIR)/select-module.so
$(OBJDIR)/select-module.so: select-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/select-module.c -o select-module.so $(LIBS)
fcntl-module.so: $(OBJDIR) $(OBJDIR)/fcntl-module.so
$(OBJDIR)/fcntl-module.so: fcntl-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/fcntl-module.c -o fcntl-module.so $(LIBS)
varray-module.so: $(OBJDIR) $(OBJDIR)/varray-module.so
$(OBJDIR)/varray-module.so: varray-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/varray-module.c -o varray-module.so $(LIBS)
pcre-module.so: $(OBJDIR) $(OBJDIR)/pcre-module.so
$(OBJDIR)/pcre-module.so: pcre-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(PCRE_INC) $(SRCDIR)/pcre-module.c -o pcre-module.so $(PCRE_LIB) $(LIBS)
onig-module.so: $(OBJDIR) $(OBJDIR)/onig-module.so
$(OBJDIR)/onig-module.so: onig-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(ONIG_INC) $(SRCDIR)/onig-module.c -o onig-module.so $(ONIG_LIB) $(LIBS)
png-module.so: $(OBJDIR) $(OBJDIR)/png-module.so
$(OBJDIR)/png-module.so: png-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(PNG_INC) $(SRCDIR)/png-module.c -o png-module.so $(PNG_LIB) $(LIBS)
socket-module.so: $(OBJDIR) $(OBJDIR)/socket-module.so
$(OBJDIR)/socket-module.so: socket-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/socket-module.c -o socket-module.so $(SOCKET_LIBS) $(LIBS)
iconv-module.so: $(OBJDIR) $(OBJDIR)/iconv-module.so
$(OBJDIR)/iconv-module.so: iconv-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(ICONV_INC) $(SRCDIR)/iconv-module.c -o iconv-module.so $(ICONV_LIB) $(LIBS)
zlib-module.so: $(OBJDIR) $(OBJDIR)/zlib-module.so
$(OBJDIR)/zlib-module.so: zlib-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(ZLIB_INC) $(SRCDIR)/zlib-module.c -o zlib-module.so $(ZLIB_LIB) $(LIBS)
fork-module.so: $(OBJDIR) $(OBJDIR)/fork-module.so
$(OBJDIR)/fork-module.so: fork-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/fork-module.c -o fork-module.so $(LIBS)
sysconf-module.so: $(OBJDIR) $(OBJDIR)/sysconf-module.so
$(OBJDIR)/sysconf-module.so: sysconf-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/sysconf-module.c -o sysconf-module.so $(LIBS)
csv-module.so: $(OBJDIR) $(OBJDIR)/csv-module.so
$(OBJDIR)/csv-module.so: csv-module.c config.h
	cd $(OBJDIR) && $(CC_SHARED) $(INCS) $(SRCDIR)/csv-module.c -o csv-module.so $(LIBS)

# Note that Windows/Cygwin modules need execute permissions
install: all
	-$(MKINSDIR) $(DEST_MODULEDIR)
	@for i in $(MODULES); \
	do \
		echo $(INSTALL_MODULE) $(OBJDIR)/$$i $(DEST_MODULEDIR); \
		$(INSTALL_MODULE) $(OBJDIR)/$$i $(DEST_MODULEDIR); \
	done
	-$(MKINSDIR) $(DEST_SLSH_DIR)
	@for i in $(SLFILES); \
	do \
		echo $(INSTALL_DATA) $$i.sl $(DEST_SLSH_DIR); \
		$(INSTALL_DATA) $$i.sl $(DEST_SLSH_DIR); \
	done
	-$(MKINSDIR) $(DEST_CMAPSDIR)
	@for i in cmaps/*.map; \
	do \
		echo $(INSTALL_DATA) $$i $(DEST_CMAPSDIR); \
		$(INSTALL_DATA) $$i $(DEST_CMAPSDIR); \
	done
	-$(MKINSDIR) $(DEST_HELPDIR)
	@for i in help/*.hlp; \
	do \
		echo $(INSTALL_DATA) $$i $(DEST_HELPDIR); \
		$(INSTALL_DATA) $$i $(DEST_HELPDIR); \
	done
clean:
	-cd $(OBJDIR) && /bin/rm -f $(MODULES)
	-/bin/rm -f *~
distclean: clean
	-/bin/rm -f Makefile

.PHONY: $(MODULES) clean distclean all install
