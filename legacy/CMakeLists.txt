cmake_minimum_required(VERSION 2.8)

project(cse576-2020sp-HW1)

set(CMAKE_CXX_FLAGS "-fdiagnostics-color=always -std=c++11 -pthread -O3 -g -march=native -fPIC")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/..)


add_library(uwimg++ SHARED
        legacy/utils.cpp
        legacy/utils.h
        legacy/image.h
        legacy/load_image.cpp
        legacy/stb_image.h
        legacy/stb_image_write.h

        legacy/access_image.cpp    # file to submit
        legacy/process_image.cpp   # file to submit
     
     
     )


link_libraries(uwimg++ m stdc++)

add_executable(test0_legacy src/test/test0.cpp)

