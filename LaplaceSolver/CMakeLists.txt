cmake_minimum_required(VERSION 3.15)
project(LaplaceSolver CXX)

set(CMAKE_CXX_STANDARD 11)

find_package(OpenMP REQUIRED)

file(GLOB subdirs RELATIVE ${PROJECT_SOURCE_DIR} CONFIGURE_DEPENDS LaplaceSolver_*)

foreach(subdir ${subdirs})
    unset(sources)
    aux_source_directory(${subdir} sources)
    add_executable(${subdir} ${sources})
    target_link_libraries(${subdir} PUBLIC OpenMP::OpenMP_CXX)
endforeach()
