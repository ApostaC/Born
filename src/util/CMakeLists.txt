project(Generic-IO-util)
cmake_minimum_required(VERSION 2.8)
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/../cpp)

link_directories( "${GENERIC_EXPORT_LIB_DIRS}")
set(UTILS Wavelet Vel Data Add)

foreach(util ${UTILS})
  ADD_EXECUTABLE(${util} ${util}.cc)				#GENERATE EXECUTABLE FOR (util).cc
  TARGET_LINK_LIBRARIES(${util} genericCpp hypercube)		#LINK HYPERCUBE AND GENERICIO
  foreach(lib ${GENERIC_EXPORT_LIBS})
    TARGET_LINK_LIBRARIES(${util} ${lib})			#LINK OTHER REQUIRED LIBS
  endforeach(lib)
  install(TARGETS ${util} DESTINATION bin)			#INSTALL
endforeach(util)
