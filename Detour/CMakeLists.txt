set(
    headers
    Include/DetourAlloc.h
    Include/DetourAssert.h
    Include/DetourCommon.h
    Include/DetourMath.h
    Include/DetourNavMesh.h
    Include/DetourNavMeshBuilder.h
    Include/DetourNavMeshQuery.h
    Include/DetourNode.h
    Include/DetourStatus.h
)

add_library(
    detour
    Source/DetourAlloc.cpp
    Source/DetourCommon.cpp
    Source/DetourNavMeshBuilder.cpp
    Source/DetourNavMesh.cpp
    Source/DetourNavMeshQuery.cpp
    Source/DetourNode.cpp
    ${headers}
)

target_include_directories(
    detour PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/Include>"
)

install(
    TARGETS detour
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
