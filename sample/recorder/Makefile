# Hisilicon Hi3516 sample Makefile

include ../Makefile.param
#ifeq ($(SAMPLE_PARAM_FILE), )
#     SAMPLE_PARAM_FILE:=../Makefile.param
#     include $(SAMPLE_PARAM_FILE)
#endif

# target source
SRC  := $(wildcard *.c) 
OBJ  := $(SRC:%.c=%.o)

TARGET := $(OBJ:%.o=%)
.PHONY : clean all

all: $(TARGET) $(OBJ)

MPI_LIBS := $(REL_LIB)/libmpi.a
OPENCV_FLAGS := -lpthread -lrt `pkg-config --libs --cflags hisiv100-opencv`

$(OBJ): %.o: %.c
	$(CC) $(CFLAGS)  -lpthread -lmath -lm -c -o $@ $^ $(MPI_LIBS) $(AUDIO_LIBA) $(SENSOR_LIBS)  -lstdc++

$(TARGET):%:%.o $(COMM_OBJ) $(A_OBJ)
	$(CC) $(CFLAGS)  -lpthread -lm -o $@ $^ $(MPI_LIBS) $(AUDIO_LIBA) $(SENSOR_LIBS) -lstdc++

clean:
	@rm -f $(TARGET)
	@rm -f $(OBJ)
	@rm -f $(COMM_OBJ)

cleanstream:
	@rm -f *.h264
	@rm -f *.jpg
	@rm -f *.mjp
	@rm -f *.mp4
