set( PLUGINS_COMMON_PATH ${CMAKE_SOURCE_DIR}/sample_plugins/plugins_common_files )

include_directories (
  ${CMAKE_SOURCE_DIR}/sample_common/include
  ${CMAKE_SOURCE_DIR}/sample_plugins/rotate_cpu/include
)

set(LDFLAGS "${LDFLAGS} -Wl,--version-script=${PLUGINS_COMMON_PATH}/mfx_plugin.map" )

list(APPEND sources.plus "${PLUGINS_COMMON_PATH}/mfx_plugin_module.cpp")
list( APPEND LIBS sample_common)

set(DEPENDENCIES libmfx dl)
make_library(sample_rotate_plugin none shared)
