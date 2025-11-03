#Makefile for Ncs2Mef project
ALL = main.c

SRCDIR = src/
BINDIR = bin/
INCLUDE = include/
EXT = c

CXX = gcc
#CXXFLAGS = -m64 -Wunused-variable -Wuninitialized
CXXFLAGS = -m64 -g

# Files
SRCFILES = convert_ncs.c write_mef_channel.c $(MEFLIB_DIR)/meflib.c $(MEFLIB_DIR)/mefrec.c
SRCS = $(wildcard $(SRCDIR)*.$(EXT))
OBJS = $(patsubst $(SRCDIR)%.$(EXT), $(BINDIR)%.o, $(SRCS))
DEPS = $(OBJS:.o=.d)
XOBJS = $(filter-out $(patsubst %, $(BINDIR)%.o, $(ALL)), $(OBJS))

# Executable files
all: $(ALL)

$(ALL): %: $(BINDIR)%.o $(XOBJS)
	$(CXX) $(CXXFLAGS) -o -I $(INCLUDE) -DOUTPUT_TO_MEF2 $@ $^


# Dependency files (header files)
$(BINDIR)%.d: $(SRCDIR)%.$(EXT)
	mkdir -p $(BINDIR)
	$(CXX) $(CXXFLAGS) -I $(INCLUDE) -DOUTPUT_TO_MEF2 $< -MM -MT $(patsubst $(SRCDIR)%.$(EXT), $(BINDIR)%.o, $<) -MF $@

# Object files
-include $(DEPS)

$(BINDIR)%.o: $(SRCDIR)%.$(EXT)
	$(CXX) $(CXXFLAGS) -c -o $@ $<

# Phony
.PHONY: all clean dist-clean

clean:
	rm -rf $(BINDIR)

dist-clean: clean
	rm -rf $(ALL)

mef2: src/main.c
	$(CC) -o Ncs2Mef2 $(CFLAGS) -I $(INCLUDE) -DOUTPUT_TO_MEF2 $(SRCS)

read:
	$(CC) -o ReadMef2 $(CFLAGS) -I $(INCLUDE) -DOUTPUT_TO_MEF2 $(SRCS)


