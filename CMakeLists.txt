cmake_minimum_required(VERSION 3.8)

project(vulcan_hello_triangle)

set(VULCAN_SDK_PATH C:/VulkanSDK/1.2.170.0)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/third-party)
add_library(Vulcan STATIC IMPORTED) 
set_property(TARGET Vulcan PROPERTY IMPORTED_LOCATION ${VULCAN_SDK_PATH}/Lib/vulkan-1.lib)

add_executable(${PROJECT_NAME}
    src/main.c
 )

set_target_properties(${PROJECT_NAME} PROPERTIES
    C_STANDARD 11
    C_STANDARD_REQUIRED YES
    C_EXTENSIONS NO
)

target_compile_options(${PROJECT_NAME} PRIVATE
    -Wall
    $<$<CONFIG:Debug>:-MTd;-DDEBUG>
    $<$<CONFIG:Release>:-O2;-MT;-DNDEBUG>
)

target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}/third-party/glfw-3.3.1/include
    ${VULCAN_SDK_PATH}/Include
)

target_link_libraries(${PROJECT_NAME} glfw Vulcan)
