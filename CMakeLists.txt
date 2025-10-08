cmake_minimum_required(VERSION 3.16)

project(VC_lab_01_aa25-26 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


add_library(srimg++ SHARED # stands for "San Raffaele Image Library ++"
     src/utils.cpp
     src/utils.h
     src/image.h
     src/load_image.cpp
     src/stb_image.h
     src/stb_image_write.h
     
     src/access_image.cpp    # file to submit
     src/process_image.cpp   # file to submit
     )

target_compile_features(srimg++ PUBLIC cxx_std_20)

add_executable(test0 src/test/test0.cpp)
target_link_libraries(test0 PRIVATE srimg++)

# --- Legacy C++11 Target Configuration ---
# This section compiles the original code from the 'legacy/src' directory.

# Create the legacy library target (note the different name to avoid conflicts)
add_library(uwimg++
    legacy/src/access_image.cpp
    legacy/src/image.h
    legacy/src/load_image.cpp
    legacy/src/process_image.cpp
    legacy/src/stb_image.h
    legacy/src/stb_image_write.h
    legacy/src/utils.cpp
    legacy/src/utils.h
)

# Set the C++ standard for the legacy library to C++11
set_target_properties(uwimg++ PROPERTIES
    CXX_STANDARD 11
    CXX_STANDARD_REQUIRED ON
)

# Create the legacy executable (note the different name)
add_executable(test0_legacy legacy/src/test/test0.cpp)

# Link the legacy executable to the legacy library
target_link_libraries(test0_legacy PRIVATE uwimg++)


#set_target_properties(test0 PROPERTIES 
#	RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
#	)

