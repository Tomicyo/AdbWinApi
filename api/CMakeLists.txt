
set(API_SRCS
    Resource.h
    stdafx.h
    stdafx.cpp
    adb_api.h
    adb_api.cpp
    adb_api_instance.h
    adb_api_instance.cpp
    adb_interface.h
    adb_interface.cpp
    adb_winusb_api.h
    adb_endpoint_object.cpp
    adb_helper_routines.cpp
    adb_io_completion.cpp
    adb_interface_enum.cpp
    adb_legacy_endpoint_object.cpp
    adb_legacy_interface.cpp
    adb_legacy_io_completion.cpp
    adb_object_handle.cpp
    AdbWinApi.cpp
    AdbWinApi.rc
)

source_group(Api FILES ${API_SRCS})
add_library(AdbApi SHARED ${API_SRCS})
target_compile_definitions(AdbApi PRIVATE UNICODE WINVER=0x0600 _WIN32_WINNT=0x0600 _WIN32_WINDOWS=0x0600 ADBWIN_EXPORTS _CRT_NON_CONFORMING_SWPRINTFS _CRT_SECURE_NO_WARNINGS)
add_msvc_pch(AdbApi "stdafx.h" "stdafx.cpp")
target_link_libraries(AdbApi setupapi Winusb)