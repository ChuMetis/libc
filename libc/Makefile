# 移植方法
# ==============================================================================
#  - edit Makefile to detect the architecture
#  - create a directory for the architecture, and put a Makefile.add in it.
#    Look at the other Makefile.adds for guidance.
#  - provide start.S (the start code, look at glibc)
#  - provide unified.S (the unified syscall)
#  - provide syscalls.h (the syscall numbers, from asm/unistd.h)
#  - provide setjmp and longjmp
#  - edit include/setjmp.h
#  - pipe, clone and mmap often need special care
#  - edit include/sys/ioctl.h
#  - edit include/sys/ptrace.h
#  - edit include/asm/sigcontext.h
#  - edit include/sys/ucontext.h
#  - edit include/endian.h
#  - edit include/fcntl.h
#  - edit include/sys/mman.h
#  - edit include/sys/shm.h
#  - edit include/sys/stat.h
#  - edit include/errno.h
#  - edit syscalls.h
#  - edit include/termios.h
#  - edit diet.c to make it recognize the architecture and add proper CFLAGS
#  - edit libcompat/syscall.S
#  - edit include/fenv.h
# ==============================================================================

user-y := libc.a

# provide start.S (the start code, look at glibc)
#
# This file(start.S) creates crt0.o, which is included in every application. 
# It should define the symbol _start, and then call the main() function, 
# possibly after setting up process-space segment selectors and pushing argc and argv onto the stack. 
# A simple implementation is:
# 
libc-y := start.o

# provide unified.S (the unified syscall)
libc-y += syscalls.s/unified.o

# provide syscalls.h (the syscall numbers, from asm/unistd.h)

libc-y += $(SYSCALLOBJ)
#LIBOBJ := lib/__v_printf.o
LIBOBJ := lib/strlen.o
libc-y += $(LIBOBJ)
libc-y += $(LIBSTDIOOBJ)
libc-y += $(LIBUGLYOBJ)
libc-y += $(LIBCRUFTOBJ)
libc-y += $(LIBCRYPTOBJ)
libc-y += $(LIBSHELLOBJ)
libc-y += $(LIBREGEXOBJ)

# provide setjmp and longjmp, edit include/setjmp.h
libc-y += lib/__longjmp.o
#libc-y += setjmp.o

# pipe, clone and mmap often need special care
libc-y += syscalls.s/clone.o


