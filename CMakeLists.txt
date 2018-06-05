cmake_minimum_required(VERSION 2.8)
project(toluapp)
enable_testing()

find_library(LIBLUA53 
             NAMES lua53
             HINTS ${LUA_SEARCH_PATH}
             )
             
find_library(LIBLUA53_DBG
             NAMES lua53_d liblua53_d liblua53-d lua53-d
             HINTS ${LUA_SEARCH_PATH_DBG}
            )
if(NOT ${LIBLUA53_DBG})
    set(LIBLUA53_DBG ${LIBLUA53}) #in case we do not have a debug lib
endif()
            
add_subdirectory(src)