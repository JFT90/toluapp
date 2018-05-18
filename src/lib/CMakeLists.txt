add_library(libtolua++
	tolua_event.c
	tolua_is.c
	tolua_map.c
	tolua_push.c
	tolua_to.c
)

set_target_properties(libtolua++ PROPERTIES OUTPUT_NAME "tolua++")

install(TARGETS libtolua++ DESTINATION ${CMAKE_BINARY_DIR} EXPORT TOLUAPPExp)
export(TARGETS libtolua++ FILE ${FIND_PACKAGE_SCRIPT_PATH}/TOLUAPP-config.cmake)