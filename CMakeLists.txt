cmake_minimum_required(VERSION 3.0)

project("vk_loader")

file(GLOB VULKAN_HEADERS "vulkan/*.h" "vulkan/*.hpp")
file(GLOB LOADER_SOURCES "vk_loader/*.h" "vk_loader/*.cpp")

add_library(vk_loader STATIC ${VULKAN_HEADERS} ${LOADER_SOURCES})
if (UNIX)
    target_link_libraries(vortex2d PRIVATE dl)
endif (UNIX)
target_include_directories(vk_loader PUBLIC ./)
target_compile_features(vk_loader PRIVATE cxx_nullptr)

