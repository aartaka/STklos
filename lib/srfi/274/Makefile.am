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


COMP ?= ../../../utils/tmpcomp
STKLOS_BINARY ?= ../../../src/stklos
STKLOS_FLAGS   = --no-init-file --case-sensitive
SO = @SH_SUFFIX@

SRC_STK = base.stk internal.stk 41.stk 134.stk 158.sk

SRC_OSTK = base.ostk internal.ostk 41.ostk 134.ostk 158.ostk

srfi_OBJS = $(SRC_OSTK)


DOCDB  = ../../DOCDB
BASEDIR= ../../..
SOURCES= $(SRC_C) $(SRC_STK) $(SRC_C_STK)


#======================================================================
srfidir       = @SCMDIR@/srfi/160
srfilibdir    = @EXECDIR@/srfi/160
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
base.stk: internal.ostk
41.stk: internal.ostk ../41.ostk
134.ostk: internal.ostk ../134.ostk
274.ostk: internal.ostk ../274.ostk


../41.ostk:
	(cd ..; $(MAKE) 41.ostk)
../134.ostk:
	(cd ..; $(MAKE) 134.ostk)
../158.ostk:
	(cd ..; $(MAKE) 158.ostk)


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
