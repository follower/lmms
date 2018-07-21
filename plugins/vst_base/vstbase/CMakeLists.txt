BUILD_PLUGIN(vstbase
	../vst_base.cpp ../VstPlugin.cpp ../VstPlugin.h ../communication.h
	MOCFILES ../VstPlugin.h
	EXPORT_BASE_NAME vstbase
	LINK SHARED
)

TARGET_INCLUDE_DIRECTORIES(vstbase
	PUBLIC ../
)

IF(LMMS_BUILD_APPLE)
	SET_TARGET_PROPERTIES(vstbase PROPERTIES LINK_FLAGS "-undefined dynamic_lookup")
ENDIF()

IF(LMMS_BUILD_LINUX)
	TARGET_LINK_LIBRARIES(vstbase qx11embedcontainer)
ENDIF()
