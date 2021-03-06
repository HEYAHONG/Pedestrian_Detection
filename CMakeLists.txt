cmake_minimum_required(VERSION 2.8)
project( Pedestrian_Detection )
find_package( OpenCV REQUIRED )
find_package(Threads REQUIRED)

add_executable( CropImage crop_image.cpp )
target_link_libraries( CropImage ${OpenCV_LIBS} )

add_executable( SvmTrainUseHog main.cpp )
target_link_libraries( SvmTrainUseHog ${OpenCV_LIBS} )

add_executable( GetHardExample find_save_HardExample.cpp )
target_link_libraries( GetHardExample ${OpenCV_LIBS} )

add_executable( ImageDetect image_detect.cpp )
target_link_libraries( ImageDetect ${OpenCV_LIBS} )

add_executable( VideoDetect video_detect.cpp )
target_link_libraries( VideoDetect ${OpenCV_LIBS} )
set_property(TARGET  VideoDetect PROPERTY COMPILE_OPTIONS "-pthread")
set_property(TARGET  VideoDetect PROPERTY INTERFACE_COMPILE_OPTIONS "-pthread")
target_link_libraries(VideoDetect "${CMAKE_THREAD_LIBS_INIT}")
add_executable( PeopleDetect peopledetect.cpp )
target_link_libraries( PeopleDetect ${OpenCV_LIBS} )
