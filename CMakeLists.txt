cmake_minimum_required(VERSION 3.18)
project(numsr_patches)

# Create a hook to add librealsense to the python path
message(AUTHOR_WARNING "Need to find python path better")
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/pyrealsense_path.dsv "prepend-non-duplicate;PYTHONPATH;lib/python3.10")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/pyrealsense_path.dsv DESTINATION share/${PROJECT_NAME}/hook)
