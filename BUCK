include_defs('//BUCKAROO_DEPS')

# DL_IMPORT?
genrule(
  name = 'pyconfig.h',
  out = 'pyconfig.h',
  cmd = 'touch $OUT',
)

# TODO: Inject Python version
genrule(
  name = 'patchlevel.h',
  out = 'patchlevel.h',
  cmd = 'echo "#define PY_MAJOR_VERSION 2 \n#define PY_MINOR_VERSION 7 \n#define PY_MICRO_VERSION 13" > $OUT',
)

cxx_library(
  name = 'boost-python',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', 'boost/**/*.hpp'),
  ]),
  headers = {
    'pyconfig.h': ':pyconfig.h',
    'patchlevel.h': ':patchlevel.h',
  },
  srcs = glob([
    'src/**/*.cpp',
  ]),
  visibility = [
    'PUBLIC',
  ],
  deps = BUCKAROO_DEPS,
)

prebuilt_cxx_library(
  name = 'boost-python-headers',
  header_only = True,
  header_namespace = 'boost',
  exported_headers = subdir_glob([
    ('include/boost', '**/*.hpp'),
  ]),
  visibility = [
    'PUBLIC',
  ],
  deps = BUCKAROO_DEPS,
)
