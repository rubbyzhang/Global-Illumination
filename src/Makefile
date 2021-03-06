#
# Unix/Linux makefile for assignment #1
#



#
# List of source files
#

PHOTONMAP_SRCS=photonmap.cpp render.cpp raytracer.cpp photontracer.cpp montecarlo.cpp \
	utils/io_utils.cpp utils/graphics_utils.cpp utils/illumination_utils.cpp \
	utils/photon_utils.cpp
PHOTONMAP_OBJS=$(PHOTONMAP_SRCS:.cpp=.o)

VIZ_SRCS=visualize.cpp
VIZ_OBJS=$(VIZ_SRCS:.cpp=.o)


#
# Compile and link options
#

CC=g++
CPPFLAGS=-Wall -I. -O3 -DNDEBUG -std=c++17
LDFLAGS=


#
# Pkg Libraries
#

PHOTONMAP_LIBS= \
  R3Graphics/libR3Graphics.a \
  R3Shapes/libR3Shapes.a \
  R2Shapes/libR2Shapes.a \
  RNBasics/libRNBasics.a \
  png/libpng.a \
  jpeg/libjpeg.a

VIZ_LIBS= \
  R3Graphics/libR3Graphics.a \
  R3Shapes/libR3Shapes.a \
  R2Shapes/libR2Shapes.a \
  RNBasics/libRNBasics.a \
  fglut/libfglut.a \
  png/libpng.a \
  jpeg/libjpeg.a


#
# OpenGL Libraries
#

OS=$(shell uname -s)
ifeq ("$(findstring CYGWIN,$(OS))", "CYGWIN")
OPENGL_LIBS=-lglu32 -lopengl32 -lwinmm -lgdi32
else ifeq ("$(OS)","Darwin")
OPENGL_LIBS=-framework GLUT -framework opengl
else
OPENGL_LIBS=-lGLU -lGL
endif



#
# Compile command
#

%.o: %.cpp
	    $(CC) $(CPPFLAGS) -c $< -o $@



#
# GNU Make: targets that don't build files
#

.PHONY: all clean distclean



#
# Make targets
#

all: $(PHOTONMAP_LIBS) $(VIZ_LIBS) photonmap visualize

photonmap: $(PHOTONMAP_LIBS) $(PHOTONMAP_OBJS)
	    $(CC) -o photonmap $(CPPFLAGS) $(LDFLAGS) $(PHOTONMAP_OBJS) $(PHOTONMAP_LIBS) $(OPENGL_LIBS) -lm

visualize: $(VIZ_LIBS) $(VIZ_OBJS)
	    $(CC) -o visualize $(CPPFLAGS) $(LDFLAGS) $(VIZ_OBJS) $(VIZ_LIBS) $(OPENGL_LIBS) -lm

R3Graphics/libR3Graphics.a:
	    cd R3Graphics; make

R3Shapes/libR3Shapes.a:
	    cd R3Shapes; make

R2Shapes/libR2Shapes.a:
	    cd R2Shapes; make

RNBasics/libRNBasics.a:
	    cd RNBasics; make

fglut/libfglut.a:
	    cd fglut; make

png/libpng.a:
	    cd png; make

jpeg/libjpeg.a:
	    cd jpeg; make

clean:
	    ${RM} -f */*.a */*/*.a *.o */*.o */*/*.o photonmap photonmap.exe visualize visualize.exe $(PHOTONMAP_LIBS) $(VIZ_LIBS)

distclean:  clean
	    ${RM} -f *~
