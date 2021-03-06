add_llvm_library (seahorn.LIB 
  LoadCrab.cc
  LiveSymbols.cc 
  SymStore.cc
  SymExec.cc
  UfoSymExec.cc
  ClpSymExec.cc
  HornifyModule.cc 
  HornifyFunction.cc 
  FlatHornifyFunction.cc
  HornWrite.cc
  HornSolver.cc
  HornCex.cc
  ClpWrite.cc
  HornClauseDB.cc
  HornClauseDBTransf.cc
  ZOption.cc
  )


# no need to link with static libraries
if (HAVE_CRAB_LLVM)
  target_link_libraries (seahorn.LIB CrabLlvmAnalysis CrabLlvmInstrumentation)
endif()

if (HAVE_LDD)
  target_link_libraries (seahorn.LIB ${LDD_LIBS})
endif()

set_target_properties (seahorn.LIB PROPERTIES OUTPUT_NAME "seahorn")

add_llvm_library(seabmc.LIB
  SymStore.cc
  LiveSymbols.cc
  SymExec.cc
  UfoSymExec.cc
  ZOption.cc
  )

set_target_properties (seabmc.LIB PROPERTIES OUTPUT_NAME "seabmc")
