project('implot', 'cpp')

cc = meson.get_compiler('cpp')
libm = cc.find_library('m', required : false)
libdl = cc.find_library('dl', required : false)

sdl_dep = dependency('sdl2')
glad_dep = dependency('glad')
imgui_dep = dependency('imgui')
imguisdl_dep = dependency('imguisdl')
imguiopengl3_dep = dependency('imguiopengl3')

implot_src = ['implot.cpp', 'implot_items.cpp']

implot_lib = static_library('implot',
    implot_src,
    dependencies: [imgui_dep, libm, libdl],
    install: true
)

executable('implot-demo',
    ['examples/demo_sdl_opengl3.cpp', 'implot_demo.cpp'],
    dependencies: [sdl_dep, glad_dep, imgui_dep, imguisdl_dep, imguiopengl3_dep, libm, libdl],
    cpp_args : ['-DIMGUI_IMPL_OPENGL_LOADER_GLAD'],
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

