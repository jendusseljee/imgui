cmake_minimum_required(VERSION 3.10)
project(imgui)

add_library(imgui STATIC
        imgui.cpp
        imgui_demo.cpp
        imgui_draw.cpp
        imgui_tables.cpp
        imgui_widgets.cpp
)

target_include_directories(imgui
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
        ${CMAKE_CURRENT_SOURCE_DIR}/backends
)

target_sources(imgui
    PRIVATE
        backends/imgui_impl_glfw.cpp
        backends/imgui_impl_opengl3.cpp
)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

target_link_libraries(imgui
    PUBLIC
        OpenGL::GL
        glfw
)
