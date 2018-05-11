
set(USB_SRCS
    Resource.h
    stdafx.h
    stdafx.cpp
    AdbWinUsbApi.rc
    AdbWinUsbApi.cpp
    adb_winusb_io_completion.h
    adb_winusb_io_completion.cpp
    adb_winusb_interface.h
    adb_winusb_interface.cpp
    adb_winusb_endpoint_object.h
    adb_winusb_endpoint_object.cpp
)

source_group(USB FILES ${USB_SRCS})

add_library(AdbUsb SHARED ${USB_SRCS})
#ADBWIN_EXPORTS
target_compile_definitions(AdbUsb PRIVATE UNICODE WINVER=0x0600 _WIN32_WINNT=0x0600 _WIN32_WINDOWS=0x0600 _CRT_NON_CONFORMING_SWPRINTFS _CRT_SECURE_NO_WARNINGS)
add_msvc_pch(AdbUsb "stdafx.h" "stdafx.cpp")
target_link_libraries(AdbUsb AdbApi setupapi Winusb)