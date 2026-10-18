cmake_minimum_required(VERSION 3.15)

project(hpx_example LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# CMP0167 is a CMake 3.30 policy. Older CMake versions do not know it.
if(POLICY CMP0167)
  cmake_policy(SET CMP0167 NEW)
endif()

find_package(HPX REQUIRED)

add_executable(simple_hpx simple_hpx.cpp)

target_link_libraries(simple_hpx PRIVATE
  HPX::hpx
  HPX::wrap_main
  HPX::iostreams_component
)
