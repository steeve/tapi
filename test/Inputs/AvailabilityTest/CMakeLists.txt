set(SOURCES
  AvailabilityTest.m
  )
set(PUBLIC_HEADERS
  AvailabilityTest.h
  )
set(PRIVATE_HEADERS
  AvailabilityTestPrivate.h
  )

SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -arch i386 -arch x86_64")
set(LIBRARY_VERSION_FLAGS "-current_version 1 -compatibility_version 1")
SET(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} ${LIBRARY_VERSION_FLAGS}")

add_library(AvailabilityTest
  SHARED
  ${PUBLIC_HEADERS}
  ${PRIVATE_HEADERS}
  ${SOURCES}
  )

target_link_libraries(AvailabilityTest
  objc
  )

set_target_properties(AvailabilityTest
  PROPERTIES
  FRAMEWORK TRUE
  FRAMEWORK_VERSION A
  PUBLIC_HEADER ${PUBLIC_HEADERS}
  PRIVATE_HEADER ${PRIVATE_HEADERS}
  INSTALL_NAME_DIR /System/Library/Frameworks
  VERSION 1
  SOVERSION 1
  )

install(TARGETS AvailabilityTest
  FRAMEWORK DESTINATION System/Library/Frameworks
  )
