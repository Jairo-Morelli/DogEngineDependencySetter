
add_library(SDL2 SHARED  "SDL.h" "SDL_main.h" "SDL2.dll" "SDL2.lib" "SDL2main.lib")

set_target_properties(SDL2 PROPERTIES LINKER_LANGUAGE CXX)

# What I think I need to do is simply link the _Dllstartup thingy to this library 


target_link_libraries(SDL2 )