cmake_minimum_required(VERSION 2.8)

if(MSVC)
  set(METIS_INSTALL FALSE)
else()
  set(METIS_INSTALL TRUE)
endif()
message(STATUS "METIS_INSTALL: ${METIS_INSTALL}")

# Configure libmetis library.
if(SHARED)
  set(METIS_LIBRARY_TYPE SHARED)
else()
  set(METIS_LIBRARY_TYPE STATIC)
endif(SHARED)

include(${GKLIB_PATH}/GKlibSystem.cmake)
# Add include directories.
include_directories(${GKLIB_PATH})
include_directories(include)
# Recursively look for CMakeLists.txt in subdirs.
add_subdirectory("include")
add_subdirectory("libmetis")
add_subdirectory("programs")
