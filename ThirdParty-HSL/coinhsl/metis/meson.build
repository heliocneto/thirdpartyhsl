if not (libmetis.found() and libmetis_version == '4')
  if fc.get_id() == 'gcc' or fc.get_id() == 'flang'
    add_global_arguments('-cpp', language : 'fortran')
  elif fc.get_id() == 'intel' or fc.get_id() == 'intel-cl' or fc.get_id() == 'nagfor'
    add_global_arguments('-fpp', language : 'fortran')
  endif
  add_global_arguments(['-Dmetis_nodend=hsl_metis', '-DMETIS_NODEND=hsl_metis'], language : 'fortran')
endif

if libmetis.found() and libmetis_version == '4'
  libhsl_src += files('metis4.f90')
elif libmetis.found() and libmetis_version == '5'
  libhsl_src += files('metis5_adapter.c', 'metis5.f90')
else
  libhsl_src += files('dummy_metis.f90')
endif
