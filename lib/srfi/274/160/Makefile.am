# Makefile for the SRFI 160
#
# Copyright © 2022 Jeronimo Pellegrini <j_p@aleph0.info>
# Based on the SRFI Makefiles by Erick Gallesio.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307,
# USA.
#
#           Author: Jeronimo Pellegrini [j_p@aleph0.info]
#    Creation date: 20-Jun-2022 09:24 (jpellegrini)

#-======================================================================


COMP ?= ../../../../utils/tmpcomp
STKLOS_BINARY ?= ../../../../src/stklos
STKLOS_FLAGS   = --no-init-file --case-sensitive
SO = @SH_SUFFIX@

SRC_STK = base.stk c128.stk c64.stk f32.stk f64.stk s16.stk \
          s32.stk s64.stk s8.stk u16.stk u32.stk u64.stk u8.stk

SRC_OSTK = base.ostk c128.ostk c64.ostk f32.ostk f64.ostk s16.ostk \
          s32.ostk s64.ostk s8.ostk u16.ostk u32.ostk u64.ostk u8.ostk


srfi_OBJS = $(SRC_OSTK)


DOCDB  = ../../DOCDB
BASEDIR= ../../..
SOURCES= $(SRC_C) $(SRC_STK) $(SRC_C_STK)


#======================================================================
srfidir       = @SCMDIR@/srfi/274/160
srfilibdir    = @EXECDIR@/srfi/274/160
srfi_DATA     = $(SRC_OSTK)
srfilib_DATA  = $(SRC_SHOBJ)
srfi_sources  = $(SRC_STK)
#======================================================================
SUFFIXES = .stk .ostk .stk -incl.c .$(SO) .c

#======================================================================

.stk.ostk:
	$(COMP) -o $*.ostk $*.stk

#======================================================================
# Dependencies
base.stk: ../internal.ostk ../../160.ostk
c64.stk:  ../internal.ostk  ../../160/c64.ostk
c128.stk: ../internal.ostk ../../160/c128.ostk
c64.stk:  ../internal.ostk ../../160/c64.ostk
f32.stk:  ../internal.ostk ../../160/f32.ostk
f64.stk:  ../internal.ostk ../../160/f64.ostk
s16.stk:  ../internal.ostk ../../160/s16.ostk
s32.stk:  ../internal.ostk ../../160/s32.ostk
s64.stk:  ../internal.ostk ../../160/s64.ostk
s8.stk:   ../internal.ostk ../../160/s8.ostk
u16.stk:  ../internal.ostk ../../160/u16.ostk
u32.stk:  ../internal.ostk ../../160/u32.ostk
u64.stk:  ../internal.ostk ../../160/u64.ostk
u8.stk:   ../internal.ostk ../../160/u8.ostk

../internal.ostk:
	(cd ..; $(MAKE) internal.ostk)
../../160/c64.ostk:
	(cd ../../160; $(MAKE) c64.ostk)
../../160/c128.ostk:
	(cd ../../160; $(MAKE) c128.ostk)
../../160/f32.ostk:
	(cd ../../160; $(MAKE) f32.ostk)
../../160/f64.ostk:
	(cd ../../160; $(MAKE) f64.ostk)
../../160/s16.ostk:
	(cd ../../160; $(MAKE) s16.ostk)
../../160/s32.ostk:
	(cd ../../160; $(MAKE) s32.ostk)
../../160/s64.ostk:
	(cd ../../160; $(MAKE) s64.ostk)
../../160/s8.ostk:
	(cd ../../160; $(MAKE) s8.ostk)
../../160/u16.ostk:
	(cd ../../160; $(MAKE) u16.ostk)
../../160/u32.ostk:
	(cd ../../160; $(MAKE) u32.ostk)
../../160/u64.ostk:
	(cd ../../160; $(MAKE) u64.ostk)
../../160/u8.ostk:
	(cd ../../160; $(MAKE) u8.ostk)


#======================================================================

install-sources:
	mkdir -p $(DESTDIR)$(srfidir)
	cp $(srfi_sources) $(DESTDIR)$(srfidir)

clean:
	rm -f $(srfi_OBJS) *-incl.c *~

distclean: clean
	rm -f Makefile

uninstall-hook:
	(cd $(PREFIX)$(srfidir) && rm -f $(srfi_sources) ) || true
	rmdir $(srfidir) || true
##
## # no docs...
## # doc:
## # 	$(STKLOS_BINARY) $(STKLOS_FLAGS) -b ../../src/boot.img \
## # 		-f ../../doc/extract-doc $(SOURCES) >> $(DOCDB)

# Local Variables:
# tab-width: 8
# End:
