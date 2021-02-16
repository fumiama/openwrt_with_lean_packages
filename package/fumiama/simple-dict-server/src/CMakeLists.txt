cmake_minimum_required(VERSION 2.6)

PROJECT(simple-dict-server C)
ADD_DEFINITIONS(-Wall -Werror --std=gnu99 -Wmissing-declarations)

SET(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")

ADD_EXECUTABLE(simple-dict-server simple-dict-server.c)
TARGET_LINK_LIBRARIES(simple-dict-server)

INSTALL(TARGETS simple-dict-server RUNTIME DESTINATION bin)
