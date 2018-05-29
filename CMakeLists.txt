cmake_minimum_required(VERSION 2.8)
project(tolua++)
enable_testing()

find_library(LIBLUA53 
             NAMES lua53
             HINTS ${LUA_SEARCH_PATH}
             )
add_subdirectory(src)