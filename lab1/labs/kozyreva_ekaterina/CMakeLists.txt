add_llvm_library(kozyrevaPrintClassesNamePlugin MODULE PrintClassPlugin.cpp PLUGIN_TOOL clang)

if(WIN32 OR CYGWIN)
  set(LLVM_LINK_COMPONENTS
    Support
  )
  clang_target_link_libraries(kozyrevaPrintClassesNamePlugin PRIVATE
    clangAST
    clangBasic
    clangFrontend
    )
endif()

set(CLANG_TEST_DEPS "kozyrevaPrintClassesNamePlugin" ${CLANG_TEST_DEPS} PARENT_SCOPE)
