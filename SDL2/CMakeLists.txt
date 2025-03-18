
add_library(SDL2 SHARED IMPORTED  "SDL.h" "SDL2.lib" "SDL2.dll")




set_target_properties(SDL2 PROPERTIES LINKER_LANGUAGE CXX)

# What I think I need to do is simply link the _Dllstartup thingy to this library 



