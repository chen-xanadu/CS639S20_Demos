cmake_minimum_required(VERSION 3.12)
project(LaplacianStencil CXX)

set(CMAKE_CXX_STANDARD 11)

find_package(OpenMP REQUIRED)

file(GLOB subdirs RELATIVE ${PROJECT_SOURCE_DIR} LaplacianStencil_*)

foreach(subdir ${subdirs})
    add_executable(${subdir} ${subdir}/Laplacian.cpp ${subdir}/main.cpp)
    target_link_libraries(${subdir} PUBLIC OpenMP::OpenMP_CXX)
endforeach()
