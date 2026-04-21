cmake_minimum_required(VERSION 3.10)
project(testapps)

# Set C and C++ standards
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set compiler flags for MISRA-C and AUTOSAR compliance
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wextra -pedantic")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -pedantic")

# C test programs
set(C_SOURCES
    c/asmtest.c
    c/eventfd1.c
    c/eventfd2.c
    c/packedstruct.c
    c/pcap.c
    c/pointertest.c
    c/popen.c
    c/readfile.c
    c/testdefine.c
    c/timer1.c
)

# C++ test programs
set(CPP_SOURCES
    c/testrecursion.cpp
    cpp/charsizetest.cpp
    cpp/explicit.cpp
    cpp/matrix1.cpp
    cpp/perf.cpp
    cpp/prioq.cpp
    cpp/prioq2.cpp
    cpp/reference.cpp
    cpp/semaphore.cpp
    cpp/setthreadname.cpp
    cpp/sharedptr.cpp
    cpp/swap.cpp
    cpp/testcppversion.cpp
    cpp/timetest.cpp
    cpp/vector-sorted.cpp
)

# Create executables for each C file
foreach(source ${C_SOURCES})
    get_filename_component(filename ${source} NAME_WE)
    add_executable(${filename} ${source})
endforeach()

# Create executables for each C++ file
foreach(source ${CPP_SOURCES})
    get_filename_component(filename ${source} NAME_WE)
    add_executable(${filename}_cpp ${source})
endforeach()
