cmake_minimum_required (VERSION 2.6)
project(kitti_native_evaluation)

include_directories(include)

add_executable(evaluate_object_offline src/evaluate_object_3d_offline.cpp)
