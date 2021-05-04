project('implot', 'cpp')

cc = meson.get_compiler('cpp')
libm = cc.find_library('m', required : false)
libdl = cc.find_library('dl', required : false)

imgui_dep = dependency('imgui')

implot_src = ['implot.cpp', 'implot_items.cpp']

implot_lib = static_library('implot',
    implot_src,
    dependencies: [imgui_dep, libm, libdl],
    install: true
)

executable('implot-demo',
    ['examples/demo_sdl_opengl3.cpp', 'implot_demo.cpp'],
    dependencies: [imgui_dep, libm, libdl],
    link_with: implot_lib,
    install: true,
)

install_headers('implot.h',)

pkg = import('pkgconfig')

pkg.generate(implot_lib,
    filebase : 'implot',
    name : 'implot',
    libraries : implot_lib,
    description : 'ImPlot library for Dear ImGui',
    url : 'https://github.com/epezent/implot',
)

