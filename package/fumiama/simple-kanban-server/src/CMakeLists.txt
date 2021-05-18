cmake_minimum_required(VERSION 2.6)

PROJECT(simple-kanban-server C)
ADD_DEFINITIONS(-Wall -Werror --std=gnu99 -Wmissing-declarations)

#SET(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")

include(TestBigEndian)
test_big_endian(isBigEndian)
if (${isBigEndian})
    add_definitions(-DWORDS_BIGENDIAN)
endif()

add_definitions(-DLISTEN_ON_IPV6)

ADD_EXECUTABLE(simple-kanban-server simple-kanban-server.c)
TARGET_LINK_LIBRARIES(simple-kanban-server spb pthread)

INSTALL(TARGETS simple-kanban-server RUNTIME DESTINATION bin)
