# Copyright (C) 2009 International Business Machines and others.
# All Rights Reserved.
# This file is distributed under the Eclipse Public License.

# $Id: Makefile.in 1135 2007-12-27 19:23:06Z andreasw $

##########################################################################
#    You can modify this example makefile to fit for your own program.   #
#    Usually, you only need to change the five CHANGEME entries below.   #
##########################################################################

# CHANGEME: This should be the name of your executable
EXE = TutorialCpp

# CHANGEME: Here is the name of all object files corresponding to the source
#           code that you wrote in order to define the problem statement
OBJS = TutorialCpp_main.o \
	TutorialCpp_nlp.o

# CHANGEME: Additional libraries
ADDLIBS =

# CHANGEME: Additional flags for compilation (e.g., include flags)
ADDINCFLAGS =

##########################################################################
#  Usually, you don't have to change anything below.  Note that if you   #
#  change certain compiler options, you might have to recompile Ipopt.   #
##########################################################################


# C++ Compiler command
CXX = clang++

# C++ Compiler options
CXXFLAGS = -O3 -pipe -DNDEBUG -Wparentheses -Wreturn-type -Wcast-qual -Wall -Wpointer-arith -Wwrite-strings -Wconversion -Wno-unknown-pragmas -Wno-long-long   -DIPOPT_BUILD

# additional C++ Compiler options for linking
CXXLINKFLAGS = 

# Include directories (we use the CYGPATH_W variables to allow compilation with Windows compilers)
INCL = `PKG_CONFIG_PATH=/Users/austen/Downloads/Ipopt-releases-3.12.7/lib64/pkgconfig:/Users/austen/Downloads/Ipopt-releases-3.12.7/lib/pkgconfig:/Users/austen/Downloads/Ipopt-releases-3.12.7/share/pkgconfig: pkg-config --cflags ipopt` $(ADDINCFLAGS)
#INCL = -I`$(CYGPATH_W) /Users/austen/Downloads/Ipopt-releases-3.12.7/include/coin`  $(ADDINCFLAGS)

# Linker flags
LIBS = `PKG_CONFIG_PATH=/Users/austen/Downloads/Ipopt-releases-3.12.7/lib64/pkgconfig:/Users/austen/Downloads/Ipopt-releases-3.12.7/lib/pkgconfig:/Users/austen/Downloads/Ipopt-releases-3.12.7/share/pkgconfig: pkg-config --libs ipopt` -lc++
##LIBS = -link -libpath:`$(CYGPATH_W) /Users/austen/Downloads/Ipopt-releases-3.12.7/lib` libipopt.lib -framework Accelerate -framework Accelerate -lm  -ldl -lc++
#LIBS = -L/Users/austen/Downloads/Ipopt-releases-3.12.7/lib -lipopt -framework Accelerate -framework Accelerate -lm  -ldl -lc++

# The following is necessary under cygwin, if native compilers are used
CYGPATH_W = echo

all: $(EXE)

.SUFFIXES: .cpp .c .o .obj

$(EXE): $(OBJS)
	bla=;\
	for file in $(OBJS); do bla="$$bla `$(CYGPATH_W) $$file`"; done; \
	$(CXX) $(CXXLINKFLAGS) $(CXXFLAGS) -o $@ $$bla $(ADDLIBS) $(LIBS)

clean:
	rm -rf $(EXE) $(OBJS) ipopt.out

.cpp.o:
	$(CXX) $(CXXFLAGS) $(INCL) -c -o $@ $<


.cpp.obj:
	$(CXX) $(CXXFLAGS) $(INCL) -c -o $@ `$(CYGPATH_W) '$<'`
