cmake_minimum_required (VERSION 3.28)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
set(Project TinyJSON)

project (${Project}
  VERSION 0.0.1
  DESCRIPTION "Very fast JSON Parser"
  LANGUAGES CXX C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)

option(TINYJSON_BUILD_TESTING "Build tests" ON)

set( Headers
  "src/TinyJSON.h"
)

set( Sources
  "src/TinyJSON.cpp"
)

# the TinyJSON library
add_library(${Project} STATIC ${Headers} ${Sources} )

if(TINYJSON_BUILD_TESTING)  
  enable_testing()
  add_subdirectory(external)
  include(CTest)
  
  add_subdirectory(tests)
endif()