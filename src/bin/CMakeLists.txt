add_executable(toluapp_bootstrap
	tolua.c
	toluabind_default.c
)

if(UNIX AND NOT APPLE)
	find_library(DL_LIBRARY dl)
	list(APPEND ${LIBLUA53} ${DL_LIBRARY})
endif()

target_link_libraries(toluapp_bootstrap
	libtoluapp
    optimized ${LIBLUA53}
    debug ${LIBLUA53_DBG}
)

file(GLOB LUA_FILES
	RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}"
	"lua/*.lua"
)

add_custom_command(OUTPUT toluabind.c
	COMMAND toluapp_bootstrap -C -o "${CMAKE_CURRENT_BINARY_DIR}/toluabind.c" tolua.pkg
	DEPENDS toluapp_bootstrap tolua.pkg ${LUA_FILES}
	WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}"
)

add_executable(toluapp
	tolua.c
	toluabind.c
)
set_target_properties(toluapp PROPERTIES DEBUG_POSTFIX "_d")
target_link_libraries(toluapp
	libtoluapp
	optimized ${LIBLUA53}
    debug ${LIBLUA53_DBG}
)
