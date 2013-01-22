cmake_minimum_required(VERSION 2.8)

project(hello)

add_executable(hello hello.cpp)

message("${CMAKE_CURRENT_SOURCE_DIR}")

find_package(LibXml2)
if (LIBXML2_FOUND)
    message("** found libxml2")
    include_directories(${LIBXML2_INCLUDE_DIR})
    message("${LIBXML2_INCLUDE_DIR}")
    target_link_libraries(hello ${LIBXML2_LIBRARIES})
else(LIBXML2_FOUND)
    message("** not found libxml2")
endif(LIBXML2_FOUND)

configure_file (
    ${CMAKE_CURRENT_SOURCE_DIR}/config.h.in
    ${CMAKE_CURRENT_SOURCE_DIR}/config.h
)

