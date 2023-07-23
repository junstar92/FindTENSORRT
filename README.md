# FindTENSORRT.cmake

Cmake script to find TensorRT Library.

# Test Environments

- Ubuntu 20.04 / NVIDIA Jetson Orin JetPack 5.0.1
- CMake >= 3.16.3
- TensorRT >= 8.4.1

# Usage

### CMake Script:
```
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
```

### Test Command:
```
$ cmake -S . -B build -DTENSORRT_ROOT_PATH=/usr/local/tensorrt
```

### Result:
```
-- The C compiler identification is GNU 10.3.0
-- The CXX compiler identification is GNU 10.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found TENSORRT: /usr/local/tensorrt/include (found version "8.4.1") 
-- TensorRT Version       : 8.4.1
-- TensorRT Root(optional): /usr/local/tensorrt
-- TensorRT Include Dir   : /usr/local/tensorrt/include
-- TensorRT Library Dir   : /usr/local/tensorrt/lib
-- nvinfer : /usr/local/tensorrt/lib/libnvinfer.so
-- nvinfer_static : /usr/local/tensorrt/lib/libnvinfer_static.a
-- nvinfer_plugin : /usr/local/tensorrt/lib/libnvinfer_plugin.so
-- nvinfer_plugin_static : /usr/local/tensorrt/lib/libnvinfer_plugin_static.a
-- nvonnxparser : /usr/local/tensorrt/lib/libnvonnxparser.so
-- nvonnxparser_static : /usr/local/tensorrt/lib/libnvonnxparser_static.a
-- nvparsers : /usr/local/tensorrt/lib/libnvparsers.so
-- nvparsers_static : /usr/local/tensorrt/lib/libnvparsers_static.a
-- nvcaffe_parser : /usr/local/tensorrt/lib/libnvcaffe_parser.so
-- Configuring done
-- Generating done
```