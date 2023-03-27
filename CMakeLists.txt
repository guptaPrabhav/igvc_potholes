cmake_minimum_required(VERSION 3.5)
project(pothole_detection_py)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(OpenCV REQUIRED)
find_package(cv_bridge REQUIRED)
find_package(image_transport REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include_directories(
  include
  ${OpenCV_INCLUDE_DIRS}
)

# set_target_properties(CXX PROPERTIES LINKER_LANGUAGE C++)

# add_executable(pothole_detection_py src/pothole_detection.py)

# target_link_libraries(pothole_detection_py
#   ${OpenCV_LIBS}
# )

# target_compile_features(pothole_detection_py PUBLIC c_std_99 cxx_std_17)

# ament_target_dependencies(pothole_detection_py
#   "rclcpp"
#   "std_msgs"
#   "sensor_msgs"
#   "OpenCV"
#   "cv_bridge"
# )

# install(TARGETS pothole_detection_py
#   DESTINATION lib/${PROJECT_NAME})

# ament_python_install_package(${PROJECT_NAME})

install(PROGRAMS
  src/pothole_detection.py
  DESTINATION lib/${PROJECT_NAME}
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
