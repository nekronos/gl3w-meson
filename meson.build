project('gl3w', 'c')

cc = meson.get_compiler('c')
host_system = host_machine.system()

gl3w_sources = [
  'include/GL/gl3w.h',
  'include/GL/glcorearb.h',
  'include/KHR/khrplatform.h',
  'src/gl3w.c',
]

if host_system == 'windows'
  dep_gl = cc.find_library('opengl32')
else
  dep_gl = dependency('gl')
endif

gl3w_include = include_directories('include')

libgl3w = static_library(
  'gl3w',
  gl3w_sources,
  include_directories : gl3w_include,
  dependencies : [dep_gl],
  install : true,
)

install_headers(
  'include/GL/gl3w.h',
  'include/GL/glcorearb.h',
  subdir : 'GL',
)

install_headers(
	'include/KHR/khrplatform.h',
	subdir: 'KHR'
)

gl3w_dep = declare_dependency(
  link_with : libgl3w,
  include_directories : gl3w_include,
)