cmake_minimum_required( VERSION 3.2 )
project( SFGUI )

set( SFGUI_MAJOR_VERSION 0 )
set( SFGUI_MINOR_VERSION 3 )
set( SFGUI_REVISION_VERSION 2 )

# Find packages.
find_package( OpenGL REQUIRED )
find_package( SFML 2.3 REQUIRED COMPONENTS graphics window system )

file(GLOB_RECURSE SFGUI_SOURCES src/*.cpp)
#add_library(SFGUI SHARED ${SFGUI_SOURCES})
add_definitions( -DSFGUI_STATIC )
add_library(SFGUI ${SFGUI_SOURCES})
set_property(TARGET SFGUI PROPERTY CXX_STANDARD 14)
target_include_directories(SFGUI PUBLIC include)
target_include_directories(SFGUI PRIVATE src)
target_include_directories(SFGUI PRIVATE src/SFGUI/Parsers/ThemeParser)
target_include_directories(SFGUI PRIVATE extlibs/libELL/include)
set_target_properties( SFGUI PROPERTIES DEFINE_SYMBOL SFGUI_EXPORTS )
