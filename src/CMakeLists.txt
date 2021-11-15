# Project source & header files
file(GLOB SOURCES
        "*.h"
        "*.cpp"
        )

set(INCLUDES ${PCAP_INCLUDE_DIR} ${MYSQL_INCLUDE_DIR})
set(LIBS ${PCAP_LIBRARIES} ${MYSQL_LIBRARIES})

if(UNIX)
  # gcc warning: scoped enums only available with -std=c++0x or -std=gnu++0
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=gnu++0x")
endif()
if( WIN32 )
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -static -static-libgcc -static-libstdc++")
  # ntohs() function in Windows but it's not working for .lib file in Windows, so I directly added lib path on the last line.
  set( LIBS ${LIBS} "Ws2_32")
endif()

include_directories(${INCLUDES})
link_libraries(${LIBS})
add_executable(kdd99extractor ${SOURCES})
#target_link_libraries(kdd99extractor ${LIBS})
target_link_libraries(kdd99extractor ${LIBS} "C:/Tools/npcap-sdk-1.11/Lib/x64/wpcap.lib")