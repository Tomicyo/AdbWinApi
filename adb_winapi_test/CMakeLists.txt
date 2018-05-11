add_executable(AdbTest 
    stdafx.cpp
    adb_winapi_test.cpp
    stdafx.h
)
target_compile_definitions(AdbTest PRIVATE WINVER=0x0600 _WIN32_WINNT=0x0600 _WIN32_WINDOWS=0x0600 _CRT_NON_CONFORMING_SWPRINTFS _CRT_SECURE_NO_WARNINGS)
add_msvc_pch(AdbTest "stdafx.h" "stdafx.cpp")
target_link_libraries(AdbTest AdbUsb)