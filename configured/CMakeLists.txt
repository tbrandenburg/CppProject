option(FOO_ENABLE "Enable Foo" ON)
if(FOO_ENABLE)
  set(FOO_STRING "foo")
endif()

option(BAR_ENABLE "Enable Bar" OFF)
if(BAR_ENABLE)
  set(BAR_STRING "bar")
endif()

configure_file(
    "config.hpp.in"
    "${CMAKE_BINARY_DIR}/configured_files/include/config.hpp" ESCAPE_QUOTES
)
