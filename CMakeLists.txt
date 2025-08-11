cmake_minimum_required(VERSION 3.30) 

project(Metal-Headers) 

file(GLOB_RECURSE HEADERS CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/include/**.hpp")
file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/source/**.cpp")

add_library(MetalHeaders STATIC) 
add_library(Metal::Headers ALIAS MetalHeaders) 

target_sources(MetalHeaders
    PRIVATE ${HEADERS} 
    PRIVATE ${SOURCES} 
)

target_include_directories(MetalHeaders
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include/
)