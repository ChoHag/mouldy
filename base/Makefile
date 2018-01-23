# There is FAR too much boilerplate in these files.
#
# Thanks, GNU, for being shit, and thanks everyone else for leaving
# GNU as the only group with anything approaching compatibility.

VERSION = 0.0

DESTDIR =
PREFIX = /
TO = $(DESTDIR)/$(PREFIX)

AR = ar
CC = cc
LD = ld

# Pre-Processor, not Plus-Plus
CPPFLAGS = -D_DEFAULT_SOURCE -D_BSD_SOURCE -D_XOPEN_SOURCE=700 -D_FILE_OFFSET_BITS=64
CFLAGS   = -static -std=c99 -Wall -pedantic
LDFLAGS  = -s
ARFLAGS  = -rcs

chmod = bin/chmod/chmod
cp = bin/cp/cp
ln = bin/ln/ln
mkdir = bin/mkdir/mkdir
test = bin/test/test

FULLBUILD = $(CC) $(CFLAGS) $(CPPFLAGS) $(LDFLAGS) $(CF_DIR) $(LF_ALL) $(LF_DIR) -o $@ $< $(LL_DIR) $(LL_ALL)
ONLYBUILD = $(CC) $(CFLAGS) $(CPPFLAGS) $(CF_DIR) -o $@ -c $<
#THENLINK  = $(LD) $(LDFLAGS) $(LF_DIR) -o $@ $^ $(LL_DIR) $(LL_ALL)
THENLINK  = $(CC) $(LDFLAGS) $(LF_DIR) -o $@ $^ $(LL_DIR) $(LL_ALL)
ENARCHIVE = $(AR) $(ARFLAGS) $@ $^
CLEANHERE = rm -f $(DIRT)
INSTALL   =                                                   \
  for bin in $(IN_BIN); do                                    \
    $(cp) $$bin $(DESTDIR)/$(PREFIX)/bin/$${bin\#\#*/};       \
    $(chmod) 0755 $(DESTDIR)/$(PREFIX)/bin/$${bin\#\#*/};     \
  done;                                                       \
  for lib in $(IN_LIB); do                                    \
    $(cp) $$lib $(DESTDIR)/$(PREFIX)/lib/$${lib\#\#*/};       \
    $(chmod) 0644 $(DESTDIR)/$(PREFIX)/lib/$${lib\#\#*/};     \
  done;                                                       \
  for inc in $(IN_INC); do                                    \
    $(cp) $$inc $(DESTDIR)/$(PREFIX)/include/$${inc\#\#*/};   \
    $(chmod) 0644 $(DESTDIR)/$(PREFIX)/include/$${inc\#\#*/}; \
  done

# Also etc, share, share/man, var

include Makefile.dir

