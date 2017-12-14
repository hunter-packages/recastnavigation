set(
    headers
    Include/Recast.h
    Include/RecastAlloc.h
    Include/RecastAssert.h
)

add_library(
    recast
    Source/Recast.cpp
    Source/RecastAlloc.cpp
    Source/RecastArea.cpp
    Source/RecastContour.cpp
    Source/RecastFilter.cpp
    Source/RecastLayers.cpp
    Source/RecastMesh.cpp
    Source/RecastMeshDetail.cpp
    Source/RecastRasterization.cpp
    Source/RecastRegion.cpp
    ${headers}
)

target_include_directories(
    recast PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/Include>"
)

install(
    TARGETS recast
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
