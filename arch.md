# Instructions

## nop - 0x01
Does nothing.
## jmp - 0x02 (ADDRESS)
Jumps to ADDRESS.

ADDRESS: 1 byte, must be in an executable segment. Will fire interupt 9 (READFAIL) if segment is unexecutable.
## map - 0x03 (ADDRESS, SIZE, LOCATION)
Maps location to memory from active drive. Requires a "des" call at some point before. Maps active drive base + LOCATION to ADDRESS for SIZE bytes.

ADDRESS: 1 byte, must be in a writable segment. Will fire interupt 6 (WRITEFAIL) if segment is read-only.
SIZE: 1 byte
LOCATION: 2 bytes, must not be out-of-bounds to the drive, will fire interupt 9 (READFAIL) if out of bounds
## out - 0x04 (BUFFER, SIZE)
Displays a string into the video monitor or serial, in that order if one fails.

BUFFER: 1 byte: Must be a register/id (1 for eax, 2 for ebx)
SIZE: 1 byte: Must not exceed location's out of bounds
## in - 0x05
Inputs a character into eax
## cmp - 0x06 (a, b)
Compares to a to b, and sets the EFLGS register accordingly. Must be absolute values not addresses, use "ptr" to use this with a memory address.

a: 1 byte
b: 1 byte
## je - 0x07 (ADDRESS)
Jump to ADDRESS if EFLGS & 0x1 (EQU) (Equal)

ADDRESS: 1 byte: must be in an executable segment. Will fire interupt 9 (READFAIL) if segment is unexecutable.
## jg - 0x08 (ADDRESS)
Jump to ADDRESS if EFLGS & 0x2 (GRT) (Greater than)

ADDRESS: 1 byte: must be in an executable segment. Will fire interupt 9 (READFAIL) if segment is unexecutable.
## jge

## push
## pop
## read
## inc
## dec
