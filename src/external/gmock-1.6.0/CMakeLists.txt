find_package(Pthreads)

set(GMOCK_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(GTEST_DIR ${GMOCK_DIR}/gtest)
set(GTEST_SOURCES ${GTEST_DIR}/src/gtest-all.cc)
set(GMOCK_SOURCES ${GMOCK_DIR}/src/gmock-all.cc)

set(GTEST_INCLUDE_DIRS ${GTEST_DIR}/include)
set(GMOCK_INCLUDE_DIRS ${GMOCK_DIR}/include ${GTEST_INCLUDE_DIRS})

include_directories(${GTEST_INCLUDE_DIRS})
include_directories(${GTEST_DIR})
include_directories(${GMOCK_INCLUDE_DIRS})
include_directories(${GMOCK_DIR})
add_library(gmock STATIC ${GMOCK_SOURCES} ${GTEST_SOURCES})
set(GMOCK_LIBRARIES gmock ${PTHREADS_LIBRARIES} PARENT_SCOPE)
set(GTEST_LIBRARIES ${GMOCK_LIBRARIES} PARENT_SCOPE)
set(GMOCK_INCLUDE_DIRS ${GMOCK_INCLUDE_DIRS} PARENT_SCOPE)
set(GTEST_INCLUDE_DIRS ${GTEST_INCLUDE_DIRS} PARENT_SCOPE)
