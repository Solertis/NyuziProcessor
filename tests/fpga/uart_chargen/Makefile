#
# Copyright 2011-2015 Jeff Bush
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

TOPDIR=../../..

include $(TOPDIR)/build/target.mk

LIBS=-lc
SRCS=chargen.c

OBJS := $(SRCS_TO_OBJS)
DEPS := $(SRCS_TO_DEPS)

$(OBJ_DIR)/chargen.hex: $(CRT0_BARE) $(OBJS)
	$(LD) -o $(OBJ_DIR)/chargen.elf $(LDFLAGS) $(CRT0_BARE) $(OBJS) $(LIBS) -los-bare $(LDFLAGS)
	$(ELF2HEX) -o $(OBJ_DIR)/chargen.hex $(OBJ_DIR)/chargen.elf

fpgarun: chargen.hex
	$(SERIAL_BOOT) $(SERIAL_PORT) chargen.hex

run-verilator: chargen.hex
	../../../bin/verilator_model +bin=chargen.hex

clean: FORCE
	rm -f chargen.elf chargen.hex

FORCE:

-include $(DEPS)
