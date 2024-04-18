cmake_minimum_required(VERSION 3.27)
project(imgui_lib)

add_library(imgui STATIC
        src/imgui.cpp
        src/imgui_demo.cpp
        src/imgui_draw.cpp
        src/imgui_impl_glfw.cpp
        src/imgui_impl_opengl3.cpp
        src/imgui_tables.cpp
        src/imgui_widgets.cpp)

target_include_directories(imgui PUBLIC include)

find_package(PkgConfig REQUIRED)
find_package(OpenGL REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

target_include_directories(imgui PUBLIC ${GLFW_INCLUDE_DIRS} ${OpenGL_INCLUDE_DIRS})
target_link_directories(imgui PUBLIC ${GLFW_LIBRARY_DIRS} ${OpenGL_LIBRARY_DIRS})
target_link_libraries(imgui PUBLIC ${GLFW_LIBRARIES} ${OPENGL_LIBRARIES})