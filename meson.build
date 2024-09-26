project('ofxGamepad', 'cpp',
version : '0.0.1',
default_options : [
  'cpp_std=c++20',
  'buildtype=release',
  'optimization=3',
  'default_library=shared',
  # 'prefer_static=true',
  'b_ndebug=if-release',
  'c_args=-pipe',
  'cpp_args=-pipe',
  # 'warning_level=3'
]
)

inc = include_directories(
  'src'
)

sources = files(
  'src/ofxGamepadCamera.cpp',
  'src/ofxGamepad.cpp',
  'src/ofxGamepadHandler.cpp',
  'src/ofxGamepadLinux.cpp',
  'src/ofxGamepadOIS.cpp',
)

install_headers(
  'src/ofxGamepadCamera.h',
  'src/ofxGamepadConfigs.h',
  'src/ofxGamepad.h',
  'src/ofxGamepadHandler.h',
  'src/ofxGamepadLinux.h',
  'src/ofxGamepadOIS.h',
  subdir: 'openframeworks/addons/'
)

add_project_arguments('-D GLM_ENABLE_EXPERIMENTAL', language: 'cpp')

deps = [
  dependency('openFrameworks'),
  dependency('OIS')
]

lib = library('ofxGamepad',
  sources,
  include_directories: inc,
  dependencies: deps,
  install: true)

ofxGamepad_dep = declare_dependency(link_with: lib, include_directories: inc, dependencies: deps)

meson.override_dependency('ofxGamepad', ofxGamepad_dep)

pkg = import('pkgconfig')
pkg.generate(lib)
