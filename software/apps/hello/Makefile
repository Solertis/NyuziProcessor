#
# Copyright 2011-2017 Jeff Bush
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

TOPDIR=../../../

include $(TOPDIR)/build/target.mk

LIBS=-lc
SRCS=hello.c

OBJS := $(SRCS_TO_OBJS)
DEPS := $(SRCS_TO_DEPS)

$(OBJ_DIR)/hello.hex: $(CRT0_BARE) $(OBJS)
	$(LD) -o $(OBJ_DIR)/hello.elf $(LDFLAGS) $(CRT0_BARE) $(OBJS) $(LIBS) -los-bare $(LDFLAGS)
	$(ELF2HEX) -o $(OBJ_DIR)/hello.hex $(OBJ_DIR)/hello.elf

run: $(OBJ_DIR)/hello.hex
	$(EMULATOR) $(OBJ_DIR)/hello.hex

verirun: $(OBJ_DIR)/hello.hex
	$(VERILATOR) +bin=$(OBJ_DIR)/hello.hex

clean:
	rm -rf $(OBJ_DIR)

-include $(DEPS)

