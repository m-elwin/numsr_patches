cmake_minimum_required(VERSION 3.18)
project(numsr_patches)

# Get the location of the pyrealsense 2 python library so it
# Can be added to the python path
find_package(pyrealsense2 REQUIRED)
get_target_property(PYREALSENSE_LOCATION pyrealsense2::pyrealsense2 LOCATION)
get_filename_component(PYREALSENSE_DIR ${PYREALSENSE_LOCATION} DIRECTORY)

# Create a hook to add librealsense to the python path
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/pyrealsense_path.dsv
  "prepend-non-duplicate;PYTHONPATH;${PYREALSENSE_DIR}")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/pyrealsense_path.dsv DESTINATION share/${PROJECT_NAME}/hook)
