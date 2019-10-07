.PHONY=all run clean

PI=pi@raspberrypi.local

CC=gcc

SRC=gles2_bcm.c
EXE=gles2_bcm
DEPENDENCIES=`PKG_CONFIG_PATH=/opt/vc/lib/pkgconfig pkg-config pkg-config --cflags --libs bcm_host brcmegl brcmglesv2`

all: ${EXE}

run: ${EXE}
	scp ${EXE} ${PI}:
	ssh -t ${PI} ./${EXE}

clean:
	rm -f ${EXE}

${EXE}: ${SRC} makefile ../common/render.h
	${CC} -Os -s -Wall -Wextra -lm ${DEPENDENCIES} -o $@ $<
