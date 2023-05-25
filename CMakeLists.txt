cmake_minimum_required(VERSION 3.0.0)
project(cppmatplot VERSION 0.1.0)

option(ENABLE_VISUALIZATION "Enable visualization" ON)

if(ENABLE_VISUALIZATION)
    add_definitions(-DENABLE_VISUALIZATION)
endif()

if(ENABLE_VISUALIZATION)
    set(Python3_FIND_STRATEGY LOCATION)
    set(Python3_ROOT_DIR "/home/frank/miniconda3/envs/cppmatplot")
    find_package(Python3 COMPONENTS Development NumPy)
    include_directories(${Python3_INCLUDE_DIRS} ${Python3_NumPy_INCLUDE_DIRS})
endif()

# include(CTest)
# enable_testing()

add_executable(cppmatplot main.cpp)

if(ENABLE_VISUALIZATION)
    target_link_libraries(cppmatplot Python3::Python Python3::NumPy)
endif()

# set(CPACK_PROJECT_NAME ${PROJECT_NAME})
# set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
# include(CPack)
