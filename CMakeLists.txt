cmake_minimum_required(VERSION 3.18)
project(numsr_patches)

# Realsense does not honor CMAKE_INSTALL_PREFIX for the python libraries
# See IntelRealSense/librealsense #10820
# In the .meta file we specify the location of the python libraries and
# then this package installs them.
# We know they exist because we depend on librealsense2 in package.xml
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/../librealsense2/pythonlibs/
  DESTINATION ../librealsense2/lib/python3/dist-packages)

# We also add colcon hooks so that the librealsense2
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/python_path.dsv "prepend-non-duplicate;PYTHONPATH;${CMAKE_INSTALL_PREFIX}/../librealsense2/lib/python3/dist-packages")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/share/${PROJECT_NAME}/hook/python_path.dsv DESTINATION share/${PROJECT_NAME}/hook)

