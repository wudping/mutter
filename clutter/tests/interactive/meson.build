clutter_tests_interactive_srcdir = join_paths(clutter_srcdir, 'tests/interactive')

clutter_tests_interactive_includepath = include_directories('.')
#clutter_tests_interactive_builddir = join_paths(clutter_builddir, 'tests/interactive')

clutter_tests_interactive_c_args = [
  '-DTESTS_DATADIR="@0@"'.format(clutter_tests_interactive_srcdir),
  '-DG_DISABLE_SINGLE_INCLUDES',
  '-DGLIB_DISABLE_DEPRECATION_WARNINGS',
  '-DCOGL_DISABLE_DEPRECATION_WARNINGS',
  '-DCLUTTER_DISABLE_DEPRECATION_WARNINGS',
]
clutter_tests_interactive_c_args += clutter_debug_c_args

clutter_tests_interactive_link_args = [
  '-Wl,--export-dynamic',
]

clutter_tests_interactive_test_sources = [
  'test-texture-slicing.c',
  'test-texture-async.c',
  'test-texture-material.c',
  'test-events.c',
  'test-scale.c',
  'test-actors.c',
  'test-shader-effects.c',
  'test-script.c',
  'test-grab.c',
  'test-cogl-shader-glsl.c',
  'test-state.c',
  'test-fbo.c',
  'test-cogl-tex-tile.c',
  'test-cogl-tex-convert.c',
  'test-cogl-tex-foreign.c',
  'test-cogl-offscreen.c',
  'test-cogl-tex-polygon.c',
  'test-cogl-multitexture.c',
  'test-stage-read-pixels.c',
  'test-paint-wrapper.c',
  'test-texture-quality.c',
  'test-layout.c',
  'test-animation.c',
  'test-easing.c',
  'test-binding-pool.c',
  'test-text.c',
  'test-text-field.c',
  'test-cairo-clock.c',
  'test-cairo-flowers.c',
  'test-cogl-vertex-buffer.c',
  'test-stage-sizing.c',
  'test-scrolling.c',
  'test-swipe-action.c',
  'test-cogl-point-sprites.c',
  'test-table-layout.c',
  'test-path-constraint.c',
  'test-state-script.c',
  'test-devices.c',
  'test-content.c',
  'test-keyframe-transition.c',
  'test-bind-constraint.c',
  'test-touch-events.c',
  'test-rotate-zoom.c',
  'test-image.c',
]

gen_test_unit_names = find_program('meson/gen-test-unit-names.sh')
clutter_interactive_test_unit_names_h = custom_target('gen-test-unit-names',
  output: 'test-unit-names.h',
  input: clutter_tests_interactive_test_sources,
  command: [gen_test_unit_names, '@OUTPUT@', '@INPUT@'],
  install: false,
)

clutter_tests_interactive_sources = [
  'test-main.c',
  clutter_interactive_test_unit_names_h,
  clutter_tests_interactive_test_sources 
]

executable('test-interactive',
  sources: clutter_tests_interactive_sources,
  include_directories: [
    clutter_includes,
    clutter_tests_interactive_includepath,
  ],
  c_args: clutter_tests_interactive_c_args,
  link_args: clutter_tests_interactive_link_args,
  dependencies: [
    clutter_deps,
    libmutter_clutter_dep,
    gdk_pixbuf_dep,
  ],
  install: false,
)
