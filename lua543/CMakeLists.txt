cmake_minimum_required(VERSION 3.6)

project(lua543)

aux_source_directory(src LIB_SRC)
aux_source_directory(lua LUA_SRC)
include_directories(inc)

# lib
add_library(lua STATIC ${LIB_SRC})
add_library(lua-shared SHARED ${LIB_SRC})
# set_target_properties(lua-shared PROPERTIES OUTPUT_NAME lua)

# lua
add_executable(luaexec lua/lua.c)
target_link_libraries(luaexec lua)
set_target_properties(luaexec PROPERTIES OUTPUT_NAME lua)

# luac
add_executable(luac lua/luac.c)
target_link_libraries(luac lua)
