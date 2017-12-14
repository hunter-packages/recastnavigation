set(
    headers
    Include/DetourCrowd.h
    Include/DetourLocalBoundary.h
    Include/DetourObstacleAvoidance.h
    Include/DetourPathCorridor.h
    Include/DetourPathQueue.h
    Include/DetourProximityGrid.h
)

add_library(
    detour_crowd
    Source/DetourCrowd.cpp
    Source/DetourLocalBoundary.cpp
    Source/DetourObstacleAvoidance.cpp
    Source/DetourPathCorridor.cpp
    Source/DetourPathQueue.cpp
    Source/DetourProximityGrid.cpp
    ${headers}
)

target_include_directories(
    detour_crowd PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/Include>"
)

target_link_libraries(detour_crowd PUBLIC detour)

install(
    TARGETS detour_crowd
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
