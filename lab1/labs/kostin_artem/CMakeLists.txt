add_llvm_library(deprWarnPlugin MODULE depr_plugin.cpp PLUGIN_TOOL clang)

if(WIN32 OR CYGWIN)
  set(LLVM_LINK_COMPONENTS
    Support
  )
  clang_target_link_libraries(deprWarnPlugin PRIVATE
    clangAST
    clangBasic
    clangFrontend
    )
endif()

set(CLANG_TEST_DEPS "deprWarnPlugin" ${CLANG_TEST_DEPS} PARENT_SCOPE)