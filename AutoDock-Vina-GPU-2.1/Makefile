# Need to be modified according to different users
WORK_DIR=.
BOOST_LIB_PATH=/usr/lib/x86_64-linux-gnu
BOOST_HEADER_PATH=/usr/include  # Adjusted to parent directory of boost/
OPENCL_LIB_PATH=/usr/local/cuda
OPENCL_VERSION=-DOPENCL_2_0
GPU_PLATFORM=-DNVIDIA_PLATFORM
DOCKING_BOX_SIZE=-DSMALL_BOX

# Should not be modified
BOOST_INC_PATH=-I$(BOOST_HEADER_PATH)  # Use /usr/include for boost headers
VINA_GPU_INC_PATH=-I$(WORK_DIR)/lib -I$(WORK_DIR)/OpenCL/inc 
OPENCL_INC_PATH=-I$(OPENCL_LIB_PATH)/include
LIB1=-lboost_program_options -lboost_system -lboost_filesystem -lboost_thread -lOpenCL
LIB2=-lstdc++ -lstdc++fs
LIB3=-lm -lpthread
LIB_PATH=-L$(BOOST_LIB_PATH) -L$(OPENCL_LIB_PATH)/lib64  # Removed /stage/lib
SRC=./lib/*.cpp ./OpenCL/src/wrapcl.cpp  # Removed Boost source files
MACRO=$(OPENCL_VERSION) $(GPU_PLATFORM) $(DOCKING_BOX_SIZE) -DBOOST_TIMER_ENABLE_DEPRECATED

all: out
out: ./main/main.cpp
	g++ -o AutoDock-Vina-GPU-2-1 $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -O3 $(SRC) $(LIB1) $(LIB2) $(LIB3) $(LIB_PATH) $(MACRO) -DNDEBUG 

source: ./main/main.cpp
	g++ -o AutoDock-Vina-GPU-2-1 $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -O3 $(SRC) $(LIB1) $(LIB2) $(LIB3) $(LIB_PATH) $(MACRO) -DNDEBUG -DBUILD_KERNEL_FROM_SOURCE 

debug: ./main/main.cpp
	g++ -o AutoDock-Vina-GPU-2-1 $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -g $(SRC) $(LIB1) $(LIB2) $(LIB3) $(LIB_PATH) $(MACRO) -DBUILD_KERNEL_FROM_SOURCE 

clean:
	rm -f AutoDock-Vina-GPU-2-1
