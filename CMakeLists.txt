cmake_minimum_required(VERSION 3.20)

project(
  VulkanPlayground
  VERSION 1.0
  LANGUAGES C CXX
)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(spdlog CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
find_package(Stb REQUIRED)
find_package(Vulkan REQUIRED)

add_executable(VulkanPlayground
    "src/Main.cpp"
)

# target_precompile_headers(VulkanPlayground PRIVATE "$<$<COMPILE_LANGUAGE:CXX>:${CMAKE_CURRENT_SOURCE_DIR}/duckpch.h>")

target_include_directories(VulkanPlayground PRIVATE
    "${CMAKE_CURRENT_SOURCE_DIR}"
    "${Stb_INCLUDE_DIR}"
    "${Vulkan_INCLUDE_DIRS}"
)

target_link_libraries(VulkanPlayground PRIVATE spdlog::spdlog glm::glm glfw Vulkan::Vulkan)
