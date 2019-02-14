#
# 参考 dietlibc-0.33 实现
# 集成到 mrtos 编译系统中
#

# 如果 arch/$(ARCH) 中定义了相应的文件，则用该文件
ifeq ($(CONFIG_CORE_IS_LINUX_X86),y)
VPATH := $(srctree)/user/libmc/arch/i386:$(VPATH)
KBUILD_SUBDIR_CPPFLAGS  += -I$(srctree)/user/libmc/arch/i386
else
ifeq ($(CONFIG_CORE_IS_LINUX_AMD64),y)
VPATH := $(srctree)/user/libmc/arch/x86_64:$(VPATH)
KBUILD_SUBDIR_CPPFLAGS  += -I$(srctree)/user/libmc/arch/x86_64
else
VPATH := $(srctree)/user/libmc/arch/$(ARCH):$(VPATH)
KBUILD_SUBDIR_CPPFLAGS  += -I$(srctree)/user/libmc/arch/$(ARCH)
endif
endif


user-y := libc/
#user-y += libcompat/
#user-y += libdl/
#user-y += liblatin1/
#user-y += libm/
#user-y += libpthread/
#user-y += librpc/

