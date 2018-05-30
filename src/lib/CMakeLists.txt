add_library(libtoluapp SHARED
	tolua_event.c
	tolua_is.c
	tolua_map.c
	tolua_push.c
	tolua_to.c
)

set_target_properties(libtoluapp PROPERTIES OUTPUT_NAME "tolua++")
target_link_libraries(libtoluapp ${LIBLUA53})
install(TARGETS libtoluapp DESTINATION ${CMAKE_BINARY_DIR} EXPORT TOLUAPPExp)
export(TARGETS libtoluapp FILE ${FIND_PACKAGE_SCRIPT_PATH}/TOLUAPP-config.cmake)