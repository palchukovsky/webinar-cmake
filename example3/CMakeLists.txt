cmake_minimum_required(VERSION 3.5)

set(PATCH_VERSION "1" CACHE INTERNAL "Patch version")
set(PROJECT_VERSION 0.0.${PATCH_VERSION})

project(Example3 VERSION ${PROJECT_VERSION})

configure_file(
        config.h.in 
        ${CMAKE_CURRENT_BINARY_DIR}/config.h
)

set(SOURCES
        main.cpp
        version.cpp
)
set(HEADERS
        version.h
)

add_executable(configure ${SOURCES} ${HEADERS})
set_target_properties(
        configure PROPERTIES
        CXX_STANDARD 11
        CXX_STANDARD_REQUIRED ON
)

target_include_directories(
        configure 
        PRIVATE 
        ${CMAKE_CURRENT_BINARY_DIR}
)