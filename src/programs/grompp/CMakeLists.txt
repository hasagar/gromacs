include_directories(${CMAKE_SOURCE_DIR}/src/gromacs/gmxpreprocess)

file(GLOB GROMPP_SOURCES *.c  ../main.cpp)

add_executable(grompp ${GROMPP_SOURCES})
gmx_add_man_page(grompp)
target_link_libraries(grompp ${GMX_EXTRA_LIBRARIES} libgromacs ${GMX_EXE_LINKER_FLAGS})
set_target_properties(grompp PROPERTIES OUTPUT_NAME "grompp${GMX_BINARY_SUFFIX}")
install(TARGETS grompp DESTINATION ${BIN_INSTALL_DIR} COMPONENT runtime)
