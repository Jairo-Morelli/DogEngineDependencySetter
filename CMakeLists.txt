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


project(SDLProject CXX)


# Include sub-projects.
# here you know how to add folders 
add_subdirectory ("CMakeTest01")
add_subdirectory("FileManager")
add_subdirectory("GameObject")
add_subdirectory("Networking")
add_subdirectory("SDL2")

add_library(SDL2 SHARED IMPORTED)

set_target_properties(SDL2 PROPERTIES IMPORTED_LOCATION "C:/Users/Jairo/source/repos/CMakeTest01/SDL2/SDL2.dll")
set_target_properties(SDL2 PROPERTIES IMPORTED_IMPLIB "C:/Users/Jairo/source/repos/CMakeTest01/SDL2/SDL2.lib" IMPORTED_IMPLIB "C:/Users/Jairo/source/repos/CMakeTest01/SDL2/SDL2main.lib")


add_executable (Main "Main.cpp")


#set(SDL2_DIR "${PROJECT_SOURCE_DIR}/SDL2/")
#SDL2 Stuff
#find_package(SDL2 REQUIRED CONFIG PATHS "${SDL2_DIR}")


#configure file 
configure_file("${PROJECT_SOURCE_DIR}/SDL2/SDL_config.h.in" "${PROJECT_BINARY_DIR}/SDL2/sdl_config.h")


#Now it is time for you to link your libraries



target_include_directories(Main PUBLIC CMakeTest01 FileManager GameObject Networking SDL2)

target_link_libraries(Main CMakeTest01 FileManager GameObject Networking SDL2 "C:/Users/Jairo/source/repos/CMakeTest01/SDL2/SDL2.lib")




