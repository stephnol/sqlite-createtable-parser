cmake_minimum_required(VERSION 3.10)

project(sqlite-createtable-parser LANGUAGES C)

add_library(sqlite-createtable-parser STATIC
	sql3parse_table.c
	sql3parse_table.h
)

add_executable(sqlite-createtable-parser-test
	test/main.c
	test/sql3parse_debug.c
	test/sql3parse_debug.h
)
target_include_directories(sqlite-createtable-parser-test PRIVATE .)
target_link_libraries(sqlite-createtable-parser-test PUBLIC sqlite-createtable-parser)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT sqlite-createtable-parser-test)
