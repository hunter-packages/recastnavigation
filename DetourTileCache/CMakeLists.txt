set(
    headers
    Include/DetourTileCacheBuilder.h
    Include/DetourTileCache.h
)

add_library(
    detour_tile_cache
    Source/DetourTileCacheBuilder.cpp
    Source/DetourTileCache.cpp
    ${headers}
)

target_include_directories(
    detour_tile_cache PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/Include>"
)

target_link_libraries(detour_tile_cache PUBLIC detour)

install(
    TARGETS detour_tile_cache
    EXPORT "${TARGETS_EXPORT_NAME}"
    LIBRARY DESTINATION "lib"
    ARCHIVE DESTINATION "lib"
    RUNTIME DESTINATION "bin"
    INCLUDES DESTINATION "${include_install_dir}"
)

install(
    FILES ${headers}
    DESTINATION "${include_install_dir}"
)
