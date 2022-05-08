# init #

include ./config.mk

## general

NAME	?=dwm

CMAKER	?=$(CC)
LMAKER	?=$(CC)

RM	?=rm -f
CP	?=cp -f

## directories

DIR	?=../../
SRC	?=$(DIR)/src
OBJ	?=$(DIR)/bin
BIN	?=$(DIR)/bin
RSC	?=$(DIR)/rsc

## files

SRCS	:=$(wildcard $(SRC)/*.c)
OBJS	:=${SRCS:.c=.o}

BINS	?=$(BIN)/$(NAME).exe
MANUAL	?=$(RSC)/info/$(NAME).1

# work #

all:	print build

build:	$(OBJS)
	${CC} -o $(NAME) ${OBJS} ${LDFLAGS}

clean:
	$(RM) $(BUILD) $(OBJS)

install: all
	mkdir -p ${DESTDIR}${PREFIX}/bin
	$(CP) $(BUILD) ${DESTDIR}${PREFIX}/bin
	chmod 755 ${DESTDIR}${PREFIX}/bin/dwm
	mkdir -p ${DESTDIR}${MANPREFIX}/man1
	sed "s/VERSION/${VERSION}/g" < dwm.1 > ${DESTDIR}${MANPREFIX}/man1/dwm.1
	chmod 644 ${DESTDIR}${MANPREFIX}/man1/dwm.1

uninstall:
	rm -f ${DESTDIR}${PREFIX}/bin/dwm\
		${DESTDIR}${MANPREFIX}/man1/dwm.1

.c.o:
	${CC} -c ${CFLAGS} $<

.PHONY: all options clean dist install uninstall

# endf #
