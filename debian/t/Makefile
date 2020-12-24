ifneq (,$(filter $(DEB_HOST_ARCH),i386 amd64))
ARCHFLAGS	+= -msse2 -msse
endif
CFLAGS		+= -I. $(OPENCLFLAGS) $(ARCHFLAGS)
CXXFLAGS	+= -std=c++11 -I. $(OPENCLFLAGS) $(ARCHFLAGS)

check:
	$(MAKE) compile_opencl_h
	$(MAKE) compile_opencl_h OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_2_0_APIS
	$(MAKE) compile_opencl_h OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_1_APIS
	$(MAKE) compile_opencl_h OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_0_APIS
	$(MAKE) compile_cl_hpp
	$(MAKE) compile_cl_hpp OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_2_0_APIS
	$(MAKE) compile_cl_hpp OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_1_APIS
	$(MAKE) compile_cl_hpp OPENCLFLAGS=-DCL_USE_DEPRECATED_OPENCL_1_0_APIS

compile_opencl_h:
	$(CC) $(CPPFLAGS) $(CFLAGS) -c opencl_h.c
	$(CXX) $(CPPFLAGS) $(CXXFLAGS) -c opencl_h.cpp

compile_cl_hpp:
	$(CXX) $(CPPFLAGS) $(CXXFLAGS) -c cl_hpp.cpp

clean:
	$(RM) *.o
