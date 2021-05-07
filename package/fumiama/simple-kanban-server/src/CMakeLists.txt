cmake_minimum_required(VERSION 2.6)

PROJECT(simple-kanban-server C)
ADD_DEFINITIONS(-Wall -Werror --std=gnu99 -Wmissing-declarations)

SET(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")

ADD_EXECUTABLE(simple-kanban-server simple-kanban-server.c)
TARGET_LINK_LIBRARIES(simple-kanban-server pthread)

INSTALL(TARGETS simple-kanban-server RUNTIME DESTINATION bin)
