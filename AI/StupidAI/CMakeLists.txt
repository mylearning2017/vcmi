project(stupidAI)
cmake_minimum_required(VERSION 2.6)

include_directories(${Boost_INCLUDE_DIRS} ${CMAKE_HOME_DIRECTORY} ${CMAKE_HOME_DIRECTORY}/include ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_HOME_DIRECTORY}/lib)

set(stupidAI_SRCS
		StdInc.cpp

		main.cpp
		StupidAI.cpp
)

set(stupidAI_HEADERS
		StdInc.h

		StupidAI.h
)

add_library(StupidAI SHARED ${stupidAI_SRCS} ${stupidAI_HEADERS})
target_link_libraries(StupidAI vcmi)

set_target_properties(StupidAI PROPERTIES ${PCH_PROPERTIES})
cotire(StupidAI)

if (NOT APPLE) # Already inside vcmiclient bundle
    install(TARGETS StupidAI RUNTIME DESTINATION ${AI_LIB_DIR} LIBRARY DESTINATION ${AI_LIB_DIR})
endif()

