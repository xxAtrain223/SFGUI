cmake_minimum_required( VERSION 3.2 )
project( SFGUI )

set( SFGUI_MAJOR_VERSION 0 )
set( SFGUI_MINOR_VERSION 3 )
set( SFGUI_REVISION_VERSION 0 )

# Find packages.
find_package( OpenGL REQUIRED )
find_package( SFML 2.3 REQUIRED COMPONENTS graphics window system )

file(GLOB_RECURSE SFGUI_SOURCES src/*)
add_library(SFGUI ${SFGUI_SOURCES})
add_definitions( -DSFGUI_STATIC )
add_definitions( -DSFGUI_INCLUDE_FONT )
add_definitions( -DSFML_STATIC )
set_property(TARGET SFGUI PROPERTY CXX_STANDARD 14)
target_include_directories(SFGUI PUBLIC include)
target_include_directories(SFGUI PRIVATE src)
target_include_directories(SFGUI PRIVATE extlibs/libELL/include)
target_link_libraries(SFGUI ${SFML_LIBRARIES})
target_link_libraries(SFGUI ${OPENGL_gl_LIBRARY})
set_target_properties( SFGUI PROPERTIES DEFINE_SYMBOL SFGUI_EXPORTS )
