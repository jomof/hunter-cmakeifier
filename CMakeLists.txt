cmake_minimum_required(VERSION 3.0.2)
include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.16.15.tar.gz"
    SHA1 "6974c2150fc0d3b09de3ad1efcbf15d360647ffa"
)
project(example_project)
hunter_add_package(SDL2)
#find_package(SDL2 CONFIG REQUIRED)
#add_library(example_library SHARED example.cpp)
#target_link_libraries(example_library SDL2::SDL2-static)
#add_custom_target(copy)
#if (ANDROID) 
#  target_compile_options(example_library PRIVATE -DGL_GLEXT_PROTOTYPES)
#endif()
file(COPY ${SDL2_ROOT}/lib/libSDL2.a DESTINATION ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})
##add_custom_command(TARGET example_library PRE_BUILD
#                   COMMAND ${CMAKE_COMMAND} -E
#                   copy ${SDL2_ROOT}/lib/libSDL2.a .)



