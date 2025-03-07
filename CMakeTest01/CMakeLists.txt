# CMakeList.txt : CMake project for CMakeTest01, include source and define
# project specific logic here.
#


# Add source to this project's executable. 

add_library(CMakeTest01 STATIC "CMakeTest01.h" "CMakeTest01.cpp")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET CMakeTest01 PROPERTY CXX_STANDARD 20)
endif()



# TODO: Add tests and install targets if needed.

#target_link_libraries(FileManager  PUBLIC FileManager)


#target_include_directories(CMakeTest01 PUBLIC "${PROJECT_BINARY_DIR}" FileManager)