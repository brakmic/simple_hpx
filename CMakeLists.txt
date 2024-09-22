cmake_minimum_required(VERSION 3.15)

# Set policies and suppress developer warnings
cmake_policy(SET CMP0167 NEW)
set(CMAKE_SUPPRESS_DEVELOPER_WARNINGS 1)

project(hpx_example LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Suppress Boost warnings
set(Boost_NO_WARN_NEW_VERSIONS ON)

# Find HPX and Boost
find_package(HPX REQUIRED)
find_package(Boost 1.86 REQUIRED)

# Create executable
add_executable(simple_hpx simple_hpx.cpp)

# Link HPX and Boost components
target_link_libraries(simple_hpx HPX::hpx HPX::wrap_main HPX::iostreams_component)
