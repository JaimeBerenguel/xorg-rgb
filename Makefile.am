# Copyright 2005 Sun Microsystems, Inc.  All rights reserved.
# 
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the
# "Software"), to deal in the Software without restriction, including
# without limitation the rights to use, copy, modify, merge, publish,
# distribute, and/or sell copies of the Software, and to permit persons
# to whom the Software is furnished to do so, provided that the above
# copyright notice(s) and this permission notice appear in all copies of
# the Software and that both the above copyright notice(s) and this
# permission notice appear in supporting documentation.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
# OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
# OF THIRD PARTY RIGHTS. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
# HOLDERS INCLUDED IN THIS NOTICE BE LIABLE FOR ANY CLAIM, OR ANY SPECIAL
# INDIRECT OR CONSEQUENTIAL DAMAGES, OR ANY DAMAGES WHATSOEVER RESULTING
# FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT,
# NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION
# WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
# 
# Except as contained in this notice, the name of a copyright holder
# shall not be used in advertising or otherwise to promote the sale, use
# or other dealings in this Software without prior written authorization
# of the copyright holder.
# 


if RGB_TXT
bin_PROGRAMS = showrgb
else
bin_PROGRAMS = rgb showrgb

rgb_CFLAGS = $(RGB_CFLAGS) $(RGB_DB_DEFINES)
rgb_LDADD = $(RGB_LIBS)
rgb_SOURCES = rgb.c 
endif

rgbdir = $(db_dir)
rgb_DATA = $(db_file).txt $(RGB_DB_FILES)
RGB_DB_DEFINES = -DRGB_DB=\"$(db_dir)/$(db_file)\"

showrgb_CFLAGS = $(RGB_CFLAGS) $(RGB_DB_DEFINES)
showrgb_LDADD = $(RGB_LIBS)
showrgb_SOURCES =  showrgb.c

dist_man_MANS = \
        showrgb.man

EXTRA_DIST= \
	others/README \
	others/old-rgb.txt \
	others/raveling.txt \
	others/thomas.txt