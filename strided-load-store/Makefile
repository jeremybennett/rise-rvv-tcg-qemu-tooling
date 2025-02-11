# Makefile to generate benchmarks for whole word load/store

# Copyright (C) 2025 Embecosm Limited <www.embecosm.com>
# Contributor Jeremy Bennett <jeremy.bennett@embecosm.com>

# SPDX-License-Identifier: GPL-3.0-or-later

# Parameters that can be set
ICNT ?= 1
LOOP_CNT ?= 1000000
VOP ?= vlse8
DOSTORE ?= 0
DOMASK ?= 0
VMASK ?=
STRIDE ?= 0
STRIDE_REG ?= t3
ELEM ?= e8
LMUL ?= m1

# The tools and their flags
AS=riscv64-unknown-linux-gnu-gcc
ASFLAGS=-march=rv64gcv -DICNT="$(ICNT)" -DLOOP_CNT="$(LOOP_CNT)"  \
         -DVOP="$(VOP)" -DOMASK="$(DOMASK)" -DOSTORE="$(DOSTORE)" \
         -DVMASK="$(VMASK)" -DSTRIDE="$(STRIDE)" -DSTRIDE_REG="$(STRIDE_REG)" \
         -DELEM="$(ELEM)" -DLMUL="$(LMUL)"

CFLAGS=-march=rv64gcv -O0
LDFLAGS=-march=rv64gcv -O0

$(VOP).exe: template.S
	$(AS) $(ASFLAGS) $^ -o $@

.PHONE: clean
clean:
	$(RM) *.exe
