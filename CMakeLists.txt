cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_STANDARD 11)
include(cmake/HunterGate.cmake)

HunterGate(
    URL "https://github.com/de-nik/hunter/archive/v0.19.137.1.tar.gz"
    SHA1 "2291d5651b6999408bdc7597b4b487f97e151ca2"
)

project(lab14)

hunter_add_package(Boost COMPONENTS program_options system filesystem)
find_package(Boost CONFIG REQUIRED program_options system filesystem)

add_executable(builder ${CMAKE_CURRENT_SOURCE_DIR}/sources/builder.cpp)
target_link_libraries(builder Boost::program_options Boost::system Boost::filesystem)

install(TARGETS builder RUNTIME DESTINATION bin)
