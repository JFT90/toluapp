add_library(libtoluapp SHARED
	tolua_event.c
	tolua_is.c
	tolua_map.c
	tolua_push.c
	tolua_to.c
)

set_target_properties(libtoluapp PROPERTIES OUTPUT_NAME "toluapp")
set_target_properties(libtoluapp PROPERTIES DEBUG_POSTFIX "_d")
target_link_libraries(libtoluapp 
                      optimized ${LIBLUA53}
                      debug ${LIBLUA53_DBG})

install(TARGETS libtoluapp
		EXPORT LibtoluappExp
		RUNTIME DESTINATION bin
		LIBRARY DESTINATION lib
		ARCHIVE DESTINATION lib
		)
export(TARGETS libtoluapp FILE ${CMAKE_BINARY_DIR}/libtoluapp-config.cmake)
export(PACKAGE libtoluapp)