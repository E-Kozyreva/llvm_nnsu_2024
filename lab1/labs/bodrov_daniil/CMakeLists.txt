add_llvm_library(ClassFieldPrinter MODULE ClassPrinter.cpp PLUGIN_TOOL clang)

if(WIN32 OR CYGWIN)
  set(LLVM_LINK_COMPONENTS
    Support
  )
  clang_target_link_libraries(ClassFieldPrinter PRIVATE
    clangAST
    clangBasic
    clangFrontend
    )
endif()

set(CLANG_TEST_DEPS "ClassFieldPrinter" ${CLANG_TEST_DEPS} PARENT_SCOPE)