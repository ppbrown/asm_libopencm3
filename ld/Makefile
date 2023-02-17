
# Generate an appropriate ".ld" file for your target here.
# You have to specify the device. Either by editing, or by using
#   make DEVICE=...
#
# You can use shorter form such as stm32f4
# But you will do better with the full name like stm32f401re


DEVICE=stm32f401re

DEFS=$(shell ../scripts/genlink.py devices.data stm32f401re DEFS)


$(DEVICE).ld:
	cpp -E $(DEFS) linker.ld.S |egrep -v '^#' > $@
