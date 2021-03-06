CC	= gcc
CFLAGS	= -O3
BIN_DIR = ../bin
INC_DIR	= ../include
LIB_DIR	= ../lib
INCL	= -I$(INC_DIR) -I/usr/include/opencv2 `pkg-config --cflags opencv`			\
	  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags gsl`
LIBS	= -L$(LIB_DIR) -lfeat `pkg-config --libs opencv`		\
	  `pkg-config --libs gtk+-2.0` `pkg-config --libs gsl`
OBJ	= imgfeatures.o utils.o sift.o kdtree.o minpq.o xform.o
BIN     = siftfeat match dspfeat

all: $(BIN) libfeat.a

libfeat.a: $(OBJ)
	ar rc $(LIB_DIR)/$@ $(OBJ)
	ranlib  $(LIB_DIR)/$@

siftfeat: libfeat.a siftfeat.c
	$(CC) $(CFLAGS) $(INCL) siftfeat.c -o $(BIN_DIR)/$@ $(LIBS)

match: libfeat.a match.c
	$(CC) $(CFLAGS) $(INCL) match.c -o $(BIN_DIR)/$@ $(LIBS)

dspfeat: libfeat.a dspfeat.c
	$(CC) $(CFLAGS) $(INCL) dspfeat.c -o $(BIN_DIR)/$@ $(LIBS)

imgfeatures.o: imgfeatures.c $(INC_DIR)/imgfeatures.h
	$(CC) $(CFLAGS) $(INCL) -c imgfeatures.c -o $@

utils.o: utils.c $(INC_DIR)/utils.h
	$(CC) $(CFLAGS) $(INCL) -c utils.c -o $@

sift.o: sift.c $(INC_DIR)/sift.h
	$(CC) $(CFLAGS) $(INCL) -c sift.c -o $@

kdtree.o: kdtree.c $(INC_DIR)/kdtree.h
	$(CC) $(CFLAGS) $(INCL) -c kdtree.c -o $@

minpq.o: minpq.c $(INC_DIR)/minpq.h
	$(CC) $(CFLAGS) $(INCL) -c minpq.c -o $@

xform.o: xform.c $(INC_DIR)/xform.h
	$(CC) $(CFLAGS) $(INCL) -c xform.c -o $@

clean:
	rm -f *~ *.o core

.PHONY: clean
