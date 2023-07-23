cmake_minimum_required(VERSION 3.16)
project(TEST_CMAKE_SCRIPT
    LANGUAGES C CXX
)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}")

find_package(TENSORRT REQUIRED)

message(STATUS "TensorRT Version       : ${TENSORRT_VERSION}")
message(STATUS "TensorRT Root(optional): ${TENSORRT_ROOT_DIR}")
message(STATUS "TensorRT Include Dir   : ${TENSORRT_INCLUDE_DIR}")
message(STATUS "TensorRT Library Dir   : ${TENSORRT_LIBRARY_DIR}")
foreach(lib ${tensorrt_libs_list})
    message(STATUS "${lib} : ${TENSORRT_${lib}_LIBRARY}")
endforeach()