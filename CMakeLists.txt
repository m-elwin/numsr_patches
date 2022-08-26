cmake_minimum_required(VERSION 3.18)
project(numsr_patches)

find_package(Python REQUIRED COMPONENTS Interpreter Development)

# Create a hook to add librealsense to the python path
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/pyrealsense_path.dsv
  "prepend-non-duplicate;PYTHONPATH;lib/python${Python_MAJOR_VERSION}.${Python_MINOR_VERSION}")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/pyrealsense_path.dsv DESTINATION share/${PROJECT_NAME}/hook)
