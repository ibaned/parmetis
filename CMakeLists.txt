cmake_minimum_required(VERSION 2.8)
project(ParMETIS)

set(GKLIB_PATH ${CMAKE_CURRENT_SOURCE_DIR}/metis/GKlib)
set(METIS_PATH ${CMAKE_CURRENT_SOURCE_DIR}/metis)
set(SHARED ${BUILD_SHARED_LIBS})

# Prepare libraries.
if(SHARED)
  set(ParMETIS_LIBRARY_TYPE SHARED)
else()
  set(ParMETIS_LIBRARY_TYPE STATIC)
endif()

include(${GKLIB_PATH}/GKlibSystem.cmake)

# List of paths that the compiler will search for header files.
# i.e., the -I equivalent
include_directories(include)
include_directories(${MPI_INCLUDE_PATH})
include_directories(${GKLIB_PATH})
include_directories(${METIS_PATH}/include)

# List of directories that cmake will look for CMakeLists.txt
add_subdirectory(metis)
add_subdirectory(include)
add_subdirectory(libparmetis)
add_subdirectory(programs)

# This is for testing during development and is not being distributed
#add_subdirectory(test)
