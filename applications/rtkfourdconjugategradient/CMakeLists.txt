WRAP_GGO(rtkfourdconjugategradient_GGO_C rtkfourdconjugategradient.ggo ../rtkinputprojections_section.ggo ../rtk4Doutputimage_section.ggo ${RTK_BINARY_DIR}/rtkVersion.ggo)
ADD_EXECUTABLE(rtkfourdconjugategradient rtkfourdconjugategradient.cxx ${rtkfourdconjugategradient_GGO_C})
TARGET_LINK_LIBRARIES(rtkfourdconjugategradient RTK)

IF (RTK_USE_CUDA)
  TARGET_LINK_LIBRARIES(rtkfourdconjugategradient rtkcuda)
ENDIF (RTK_USE_CUDA)

# Installation code
IF(NOT RTK_INSTALL_NO_EXECUTABLES)
  FOREACH(EXE_NAME rtkfourdconjugategradient) 
    INSTALL(TARGETS ${EXE_NAME}
      RUNTIME DESTINATION ${RTK_INSTALL_RUNTIME_DIR} COMPONENT Runtime
      LIBRARY DESTINATION ${RTK_INSTALL_LIB_DIR} COMPONENT RuntimeLibraries
      ARCHIVE DESTINATION ${RTK_INSTALL_ARCHIVE_DIR} COMPONENT Development)
  ENDFOREACH(EXE_NAME) 
ENDIF(NOT RTK_INSTALL_NO_EXECUTABLES)

