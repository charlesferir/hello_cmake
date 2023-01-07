cmake_minimum_required(VERSION 3.0.0)
project(hello_cmake VERSION 0.1.0)

include(CTest)
enable_testing()

add_executable(hello_cmake main.cpp)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

find_package(SDL2)
find_package(box2d)

if(TARGET SDL2::SDL2)
   target_link_libraries(hello_cmake SDL2::SDL2)
endif()

if(TARGET box2d::box2d)
   target_link_libraries(hello_cmake box2d::box2d)
endif()
