set(Title "Instrumentation")
set(Student "Soloninko_Andrey")
set(Group "FIIT2")
set(PluginName "${Title}_${Student}_${Group}")

if (NOT WIN32 AND NOT CYGWIN)
    message("-- ${PluginName} -- BUILD")

    file(GLOB_RECURSE ALL_SOURCE_FILES *.cpp *.h *.hpp)
    add_llvm_pass_plugin(${PluginName} ${ALL_SOURCE_FILES}
    DEPENDS
    intrinsics_gen
    BUILDTREE_ONLY)

    set(LLVM_TEST_DEPENDS ${PluginName} ${LLVM_TEST_DEPENDS} PARENT_SCOPE)
else()
    message("-- ${PluginName} -- NOT BUILD")
endif()
