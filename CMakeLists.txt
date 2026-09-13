cmake_minimum_required(VERSION 3.16)

if (DEFINED ESP_PLATFORM)
  # idf component
  idf_component_register(
      SRC_DIRS src
      INCLUDE_DIRS src
  )

  target_compile_options(${COMPONENT_LIB} PUBLIC -Wno-error)

else()

# set the project name
project(arduino_libfoxenflac)

set(CMAKE_CXX_STANDARD 17)

file(GLOB_RECURSE SRC_LIST_C CONFIGURE_DEPENDS  "${PROJECT_SOURCE_DIR}/src/*.c" )

# define libraries
add_library (arduino_libfoxenflac ${SRC_LIST_C})

# define location for header files
target_include_directories(arduino_libfoxenflac PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src )

endif()
