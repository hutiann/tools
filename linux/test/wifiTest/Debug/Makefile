#######################################
#    Name:Makefile
#    Author:     linca
#    Date:       2013.01.28
#   Purpose:    �����ļ�
#######################################

#��������C�ļ�ʹ��GCC,cpp�ļ�ʹ��g++
CC       = arm-linux-gcc
CXX      = arm-linux-g++
#CC      = /home/linca/freescale/gcc-freescale/fsl-linaro-toolchain/bin/arm-linux-gcc
#CXX     = /home/linca/freescale/gcc-freescale/fsl-linaro-toolchain/bin/arm-linux-g++
#CC      = gcc
#CXX     = g++

#������������,-Wall:������еľ�����Ϣ -O2:�ڱ���ʱ�����Ż���-g:��ʾ����debug�İ汾
CFLAGS=-Os -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Winline -I. -I/usr/local/arm/arm-2009q3/include 
#DEPFLAGS=-MMD
DEPFLAGS=
WELIB_FLAG= -DWE_NOLIBM=y
STRIPFLAGS= -Wl,-s
WEDEF_FLAG= -DWE_ESSENTIAL=y

XCFLAGS=$(CFLAGS) $(DEPFLAGS) $(WELIB_FLAG) $(WEDEF_FLAG)

#Դ�ļ�Ŀ¼����Makefile����Ŀ¼Ϊ��Ŀ¼
SRC = ../CardDev/src               \
      ../Os/src                        \
      ../                

#ͷ�ļ�Ŀ¼����Makefile����Ŀ¼Ϊ��Ŀ¼
INCLUDE = -I ../CardDev/h          \
          -I ../Os/h                   \
		  

#���ļ�Ŀ¼����Makefile����Ŀ¼Ϊ��Ŀ¼
#LIB = -lrt -lm -static
LIB = -lm -lrt 

#���Ӳ���
LDFLAGS = $(LIB)

#����ļ�
OUTPUT = wifiTest

####################################����Ͳ��ø���########################################
#������C�ļ��������o�ļ�
%.o : %.c
#$(CC) $(XCFLAGS) $(INCLUDE) -c $< -o $@
	$(CC) $(XCFLAGS) $(STRIPFLAGS) $(INCLUDE) -c -g $< -o $@


#������Ŀ¼�µ�C/C++�ļ�����һ���б����������SOURCES
SOURCES := $(foreach dir,$(SRC),$(wildcard $(dir)/*.c))

OBJS = $(patsubst %.c,%.o,$(SOURCES))

$(OUTPUT) : $(OBJS)
	$(CC) $(OBJS) $(LDFLAGS) $(XCFLAGS) $(STRIPFLAGS) -o $(OUTPUT)
	chmod a+x $(OUTPUT)

clean:
	rm -rf $(OBJS)
	rm -rf $(OUTPUT)

#########################################################################################