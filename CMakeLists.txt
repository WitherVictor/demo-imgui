cmake_minimum_required(VERSION 3.18)
project(demo-imgui VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 23)

file(GLOB IMGUI_SOURCES thirdparty/imgui/*.cpp)
message("Found ImGui sources: ${IMGUI_SOURCES}")

add_executable(${PROJECT_NAME}
    main.cpp
    ${IMGUI_SOURCES}

    thirdparty/imgui/backends/imgui_impl_glfw.cpp
    thirdparty/imgui/backends/imgui_impl_opengl3.cpp
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    glfw
    GL
)

target_include_directories(${PROJECT_NAME} PRIVATE
    thirdparty/imgui
    thirdparty/imgui/backends
)
