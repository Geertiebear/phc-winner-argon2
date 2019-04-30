cmake_minimum_required(VERSION 3.0)
project(argon2)

SET(SOURCES src/argon2.c src/core.c src/blake2/blake2b.c
	src/thread.c src/encoding.c src/ref.c)

add_library(argon2 OBJECT ${SOURCES})
target_include_directories(argon2 PUBLIC include/)
set_property(TARGET argon2 PROPERTY POSITION_INDEPENDENT_CODE 1)
add_library(argon2_shared SHARED $<TARGET_OBJECTS:argon2>)
add_library(argon2_static STATIC $<TARGET_OBJECTS:argon2>)