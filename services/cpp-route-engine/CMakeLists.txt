cmake_minimum_required(VERSION 3.20)

project(cpp_route_engine LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

include(FetchContent)

# Fetch cpp-httplib
FetchContent_Declare(
  cpp_httplib
  GIT_REPOSITORY https://github.com/yhirose/cpp-httplib.git
  GIT_TAG v0.15.3 # 필요 시 버전 조정
)

# Fetch nlohmann/json
FetchContent_Declare(
  nlohmann_json
  GIT_REPOSITORY https://github.com/nlohmann/json.git
  GIT_TAG v3.11.3 # 필요 시 버전 조정
)

FetchContent_MakeAvailable(cpp_httplib nlohmann_json)

file(GLOB_RECURSE CPP_ROUTE_ENGINE_SOURCES
  CONFIGURE_DEPENDS
  src/*.cpp
)

add_executable(cpp_route_engine
  ${CPP_ROUTE_ENGINE_SOURCES}
)

target_include_directories(cpp_route_engine
  PRIVATE
    ${cpp_httplib_SOURCE_DIR}
)

target_link_libraries(cpp_route_engine
  PRIVATE
    nlohmann_json::nlohmann_json
)

if(MSVC)
  target_compile_options(cpp_route_engine PRIVATE /W4 /permissive-)
else()
  target_compile_options(cpp_route_engine PRIVATE -Wall -Wextra -Wpedantic)
endif()
