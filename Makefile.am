# Copyright 2008 Sun Microsystems, Inc.  All rights reserved.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice (including the next
# paragraph) shall be included in all copies or substantial portions of the
# Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
# DEALINGS IN THE SOFTWARE.
#


bin_PROGRAMS = showrgb

showrgb_SOURCES =  showrgb.c

appman_PRE = showrgb.man

if RGB_DB
bin_PROGRAMS += rgb

rgb_SOURCES = rgb.c

appman_PRE += rgb.man

$(RGB_DB_FILES): rgb rgb.txt
	-rm -f $(RGB_DB_FILES)
	./rgb rgb < $(srcdir)/rgb.txt
endif

rgbdir = $(db_dir)
rgb_DATA = $(db_file).txt $(RGB_DB_FILES)
RGB_DB_DEFINES = -DRGB_DB=\"$(db_dir)/$(db_file)\"
AM_CFLAGS = $(RGB_CFLAGS) $(RGB_DB_DEFINES) $(CWARNFLAGS)

EXTRA_DIST= \
	rgb.txt \
	others/README \
	others/old-rgb.txt \
	others/raveling.txt \
	others/thomas.txt

appmandir = $(APP_MAN_DIR)

appman_DATA = $(appman_PRE:man=@APP_MAN_SUFFIX@)

EXTRA_DIST += $(appman_PRE)
MAINTAINERCLEANFILES = ChangeLog INSTALL
CLEANFILES = $(appman_DATA) $(RGB_DB_FILES)

SED = sed

# Strings to replace in man pages
XORGRELSTRING = @PACKAGE_STRING@
  XORGMANNAME = X Version 11

MAN_SUBSTS = \
	-e 's|__RGB_DB__|$(db_dir)/$(db_file)|' \
	-e 's|__RGB_DB_DIR__|$(db_dir)|' \
	-e 's|__RGB_DB_TYPE__|$(RGB_DB_TYPE)|' \
	-e 's|__RGB_DB_FILES__|$(RGB_DB_FILES)|' \
	-e 's|__vendorversion__|"$(XORGRELSTRING)" "$(XORGMANNAME)"|' \
	-e 's|__xorgversion__|"$(XORGRELSTRING)" "$(XORGMANNAME)"|' \
	-e 's|__xservername__|Xorg|g' \
	-e 's|__xconfigfile__|xorg.conf|g' \
	-e 's|__projectroot__|$(prefix)|g' \
	-e 's|__apploaddir__|$(appdefaultdir)|' \
	-e 's|__appmansuffix__|$(APP_MAN_SUFFIX)|g' \
	-e 's|__libmansuffix__|$(LIB_MAN_SUFFIX)|g' \
	-e 's|__adminmansuffix__|$(ADMIN_MAN_SUFFIX)|g' \
	-e 's|__miscmansuffix__|$(MISC_MAN_SUFFIX)|g' \
	-e 's|__filemansuffix__|$(FILE_MAN_SUFFIX)|g'

SUFFIXES = .$(APP_MAN_SUFFIX) .man

.man.$(APP_MAN_SUFFIX):
	$(AM_V_GEN)$(SED) $(MAN_SUBSTS) < $< > $@

.PHONY: ChangeLog INSTALL

INSTALL:
	$(INSTALL_CMD)

ChangeLog:
	$(CHANGELOG_CMD)

dist-hook: ChangeLog INSTALL
