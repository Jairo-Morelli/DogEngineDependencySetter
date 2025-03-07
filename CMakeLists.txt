# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("CMakeTest01")

# Include sub-projects.
# here you know how to add folders 
add_subdirectory ("CMakeTest01")
add_subdirectory("FileManager")
add_subdirectory("GameObject")
add_subdirectory("Networking")



add_executable (Main "Main.cpp")




#Now it is time for you to link your libraries

target_link_libraries(Main PUBLIC CMakeTest01 FileManager GameObject Networking)
target_include_directories(Main PUBLIC CMakeTest01 FileManager GameObject Networking)
