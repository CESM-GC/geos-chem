add_library(Isorropia EXCLUDE_FROM_ALL isorropiaII_main_mod.F)

target_link_libraries(Isorropia PUBLIC GEOSChemBuildProperties)

target_compile_options(Isorropia PRIVATE 
  ""
  # NOTE: ISORROPIA probably needs to be compiled
  # with REAL*8 or else it'll crash
  $<$<STREQUAL:"${CMAKE_Fortran_COMPILER_ID}","Intel">:-r8>
  $<$<STREQUAL:"${CMAKE_Fortran_COMPILER_ID}","GNU">:-fdefault-real-8 -fdefault-double-8>
)

