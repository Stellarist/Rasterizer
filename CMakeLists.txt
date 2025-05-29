cmake_minimum_required(VERSION 3.20)

project(Rasterizer)

add_compile_definitions(PROJECT_PATH="${CMAKE_SOURCE_DIR}")

file(GLOB_RECURSE INC_LIST src/*.hpp)
file(GLOB_RECURSE SRC_LIST src/*.cpp)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR}/src PREFIX "Source Files" FILES ${SRC_LIST})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR}/src PREFIX "Header Files" FILES ${INC_LIST})

find_package(glad REQUIRED)
find_package(glfw3 REQUIRED)
find_package(yaml-cpp REQUIRED)

add_executable(Rasterizer 
    ${INC_LIST} 
    ${SRC_LIST}
)

target_link_libraries(Rasterizer
    glfw
    glad::glad
    yaml-cpp::yaml-cpp
)
