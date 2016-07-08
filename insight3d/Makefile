SOURCES=$(wildcard *.cpp)
OBJECTS=$(patsubst %.cpp,%.o,$(SOURCES))
DEBUG= -O3 -ggdb -Werror # -Wall XXX To be done...
ANN_INCLUDE= -I./ann_1.1.1/include/

all: insight

insight: $(OBJECTS) sift_detector ./ann_1.1.1/lib/libANN.a ./sba/libsba.a
	g++ $(DEBUG) -o insight *.o `pkg-config --libs opencv libxml-2.0 sdl gtk+-2.0` ./sift/lib/libfeat.a $(AGARLIB) -llapack -lblas -lGL -lGLU ./sba/libsba.a ./ann_1.1.1/lib/libANN.a -pthread

./ann_1.1.1/lib/libANN.a:
	make -C ann_1.1.1 linux-g++

./sba/libsba.a:
	make -C sba 

sift_detector:
	make -C ./sift

%.o: %.cpp
	g++ $(DEBUG) -c `pkg-config --cflags opencv libxml-2.0 sdl gtk+-2.0` $(ANN_INCLUDE) -I/usr/include/opencv2 $<

.PHONY: clean

clean: 
	rm -f *.o insight



