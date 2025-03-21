# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_SYSTEM_NAME  LINUX)

  
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")

endif()



set(CMAKE_TRY_COMPILE_TARGET_TYPE "STATIC_LIBRARY")

project(SDLProject CXX)




# Include sub-projects.
# here you know how to add folders 
add_subdirectory ("CMakeTest01")
add_subdirectory("FileManager")
add_subdirectory("GameObject")
add_subdirectory("Networking")
add_subdirectory("SDL2")

#set_property(TARGET SDLProject PROPERTY CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreadedDLL")


add_executable (Main "Main.cpp")


set(SDL2_DIR "C:/Users/jalbm/source/repos/CMakeTest01")


#SDL2 Stuff
find_package(SDL2 REQUIRED CONFIG)
include_directories(${SDL_INCLUDE_DIRS})




#Now it is time for you to link your libraries

target_link_libraries(Main CMakeTest01 FileManager GameObject Networking ${SDL2_LIBRARIES})

target_include_directories(Main PUBLIC CMakeTest01 FileManager GameObject Networking SDL2)
