add_llvm_library(ProkofevRenamePlugin  MODULE RenameIdentificator.cpp PLUGIN_TOOL clang)

if(WIN32 OR CYGWIN)
  set(LLVM_LINK_COMPONENTS
    Support
  )
  clang_target_link_libraries(ProkofevRenamePlugin PRIVATE
    clangAST
    clangBasic
    clangFrontend
    )
endif()

set(CLANG_TEST_DEPS "ProkofevRenamePlugin" ${CLANG_TEST_DEPS} PARENT_SCOPE)
