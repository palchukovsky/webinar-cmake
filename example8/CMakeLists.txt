cmake_minimum_required(VERSION 3.5)

project(example8)

set(SOURCES
        main.cpp
        math.cpp
)

set(HEADERS
        math.h)

add_executable(main ${SOURCES} ${HEADERS})
target_compile_features(main PUBLIC cxx_std_11)
set_target_properties(main PROPERTIES CXX_STANDARD_REQUIRED ON)

target_compile_features(
        main
        PRIVATE
        cxx_generic_lambdas
)