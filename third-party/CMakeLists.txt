cmake_minimum_required(VERSION 3.8)

# glfw
set(ENKITS_BUILD_EXAMPLES OFF CACHE BOOL "Build basic example applications")
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "GLFW lib only")
set(GLFW_BUILD_TESTS OFF CACHE BOOL "GLFW lib only")
set(GLFW_BUILD_DOCS OFF CACHE BOOL "GLFW lib only")
set(GLFW_BUILD_INSTALL OFF CACHE BOOL "GLFW lib only")
set(USE_MSVC_RUNTIME_LIBRARY_DLL OFF CACHE BOOL "Don't use GLFW runtime dll")
option(BUILD_GLFW_LIB_STATIC "Build glfw static" ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/glfw-3.3.1)
