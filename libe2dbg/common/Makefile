##
## Makefile for common (user/kernel code) parts of libe2dbg in the ERESI framework
##
## Started on  Tue Aug  16 06:32:29 2005 jfv
## $Id
##

include ../../config.h

SRC			= backtrace.c breakpoints.c display.c mode.c stack.c \
			step.c dumpregs.c dbghooks.c mutex.c dbg-ia32.c dbg-sparc32.c
OBJ32			= $(SRC:.c=.32.o)
OBJ64			= $(SRC:.c=.64.o)
CC			?= gcc
RM			= rm -f

CFLAGS32		+= -fPIC -g3 -Wall -I../include $(DYNOPT) $(BUILDOP) 	 \
			-I../../libelfsh/include/ -I../../libdump/include/       \
			-I../../libasm/include/ -I../../libstderesi/include/	 \
			-I../../libui/include/ -I../../libmjollnir/include/ 	 \
			-I../../libaspect/include -I../../librevm/include/	 \
			-I../../libedfmt/include/ -I../../liballocproxy/include/ \
			$(KERNSHINCINC) $(KERNSH) -DE2DBG_PRESENT			 \
			-DELFSH_INTERN -DE2DBG_INTERN $(ASMOPT) -DERESI32

CFLAGS64		+= -fPIC -g3 -Wall -I../include $(DYNOPT) $(BUILDOP) 	 \
			-I../../libelfsh/include/ -I../../libdump/include/       \
			-I../../libasm/include/ -I../../libstderesi/include/	 \
			-I../../libui/include/ -I../../libmjollnir/include/ 	 \
			-I../../libaspect/include -I../../librevm/include/	 \
			-I../../libedfmt/include/ -I../../liballocproxy/include/ \
			$(KERNSHINC) $(KERNSH) -DE2DBG_PRESENT			 \
			-DELFSH_INTERN -DE2DBG_INTERN $(ASMOPT) -DERESI64

all			: all32 all64

all32			: ${OBJ32}

all64			: ${OBJ64}

clean		       :
		       @$(RM) $(OBJ32) $(OBJ64) *~ \#* *\# .\#*

fclean		       : clean

%.32.o : %.c
			$(CC) $(CFLAGS32) -c -o $@ $<
%.64.o : %.c
			$(CC) $(CFLAGS64) -c -o $@ $<

