cmake_minimum_required(VERSION 3.12)

project(Example VERSION 0.0.6)

option(WITH_INFO_EXAMPLE "Hmmmm...." OFF)

add_executable(main main.cpp)

if(WITH_INFO_EXAMPLE)
        target_compile_definitions(main PRIVATE "-DWITH_INFO=1")
else()
        target_compile_definitions(main PRIVATE "-DWITH_INFO=0")
endif()

target_compile_features(main PUBLIC cxx_std_17)
set_target_properties(main PROPERTIES CXX_STANDARD_REQUIRED ON)

target_include_directories(
        main
        PRIVATE
        ${CMAKE_CURRENT_BINARY_DIR}
)

if(BUILD_EXAMPLES)
        target_link_libraries(main logger)
        target_include_directories(
                main PRIVATE
                "${CMAKE_CURRENT_SOURCE_DIR}/../src/")
else()
        find_package(logger CONFIG REQUIRED)
        target_link_libraries(main logger::logger)
endif()