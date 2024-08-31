cmake_minimum_required(VERSION 3.29)
project(StudentManager)

set(CMAKE_CXX_STANDARD 20)

include(FetchContent)
FetchContent_Declare(
        rapidcsv
        GIT_REPOSITORY "https://github.com/d99kris/rapidcsv.git"
        GIT_TAG        "v8.50"
)
FetchContent_MakeAvailable(rapidcsv)

# Find PostgreSQL client library (libpq)
find_package(PostgreSQL REQUIRED)

# Use pkg-config to find libpqxx
find_package(PkgConfig REQUIRED)
pkg_check_modules(LIBPQXX REQUIRED libpqxx)

link_directories(/opt/homebrew/lib)
include_directories(/opt/homebrew/include)

add_executable(StudentManager
        main.cpp
)

target_link_libraries(StudentManager PRIVATE rapidcsv)
target_link_libraries(StudentManager PRIVATE pqxx)



