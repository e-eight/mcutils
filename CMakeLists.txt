cmake_minimum_required(VERSION 3.1...3.14)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
  cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

project(mcutils LANGUAGES CXX)

set(HEADERS parsing.h gsl.h io.h memoizer.h profiling.h
            vector_tuple.h arithmetic.h deprecated.h eigen.h)
set(SOURCES parsing.cpp)
set(TARGET mcutils)

add_library(${TARGET} STATIC ${SOURCES} ${HEADERS})

target_link_libraries(${TARGET} PUBLIC fmt::fmt)

target_link_libraries(${TARGET} PUBLIC Eigen3::Eigen)

target_include_directories(${TARGET} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/..)
