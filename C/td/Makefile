#Makefile for Ncs2Mef project
ALL = main.c

SRCDIR = src/
BINDIR = bin/
EXT = cpp

CXX = gcc
#CXXFLAGS = -m64 -Wunused-variable -Wuninitialized
CXXFLAGS = -m64 -g

# Files
SRCS = $(wildcard $(SRCDIR)*.$(EXT))
OBJS = $(patsubst $(SRCDIR)%.$(EXT), $(BINDIR)%.o, $(SRCS))
DEPS = $(OBJS:.o=.d)
XOBJS = $(filter-out $(patsubst %, $(BINDIR)%.o, $(ALL)), $(OBJS))

# Executable files
all: $(ALL)

$(ALL): %: $(BINDIR)%.o $(XOBJS)
	$(CXX) $(CXXFLAGS) -o $@ $^









OPTFLAGS = -O3 
MAIN = main.c
MEFLIB_DIR = .
SRCFILES = convert_ncs.c write_mef_channel.c $(MEFLIB_DIR)/meflib.c $(MEFLIB_DIR)/mefrec.c
TARGET = Ncs2Mef3
INCLUDE = .


all: #full build
	$(CC) -o $(TARGET) $(CFLAGS) $(MAIN) $(SRCFILES) -I $(INCLUDE)

mef2: 
	$(CC) -o Ncs2Mef2 $(CFLAGS) -DOUTPUT_TO_MEF2 main.c convert_ncs.c write_mef_channel_mef2.c mef_lib.c
