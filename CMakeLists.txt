cmake_minimum_required(VERSION 3.21)
project(Demangle)

set(CMAKE_CXX_STANDARD 17)

add_library(Demangle
        lib/Demangle/Demangle.cpp
        lib/Demangle/DLangDemangle.cpp
        lib/Demangle/ItaniumDemangle.cpp
        lib/Demangle/MicrosoftDemangle.cpp
        lib/Demangle/MicrosoftDemangleNodes.cpp
        lib/Demangle/RustDemangle.cpp
        include/llvm/Demangle/Demangle.h
        include/llvm/Demangle/DemangleConfig.h
        include/llvm/Demangle/ItaniumDemangle.h
        include/llvm/Demangle/ItaniumNodes.def
        include/llvm/Demangle/MicrosoftDemangle.h
        include/llvm/Demangle/MicrosoftDemangleNodes.h
        include/llvm/Demangle/StringViewExtras.h
        include/llvm/Demangle/Utility.h)

target_include_directories(Demangle PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>)

# This fixes CLion intellisense
target_include_directories(Demangle PRIVATE
        include)