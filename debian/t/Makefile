CFLAGS		+= -I. $(OPENCLFLAGS) -msse2 -msse
CXXFLAGS	+= -I. $(OPENCLFLAGS) -msse2 -msse

check:
	$(MAKE) compile_opencl_h
	$(MAKE) compile_opencl_h OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_1_APIS
	$(MAKE) compile_opencl_h OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_0_APIS
	$(MAKE) compile_cl_hpp
	$(MAKE) compile_cl_hpp OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_1_APIS
	$(MAKE) compile_cl_hpp OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_0_APIS

compile_opencl_h:
	$(CC) $(CFLAGS) -c opencl_h.c
	$(CXX) $(CXXFLAGS) -c opencl_h.cpp

compile_cl_hpp:
	$(CXX) $(CXXFLAGS) -c cl_hpp.cpp

clean:
	$(RM) *.o
