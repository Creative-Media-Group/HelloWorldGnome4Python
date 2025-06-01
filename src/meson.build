pkgdatadir = get_option('prefix') / get_option('datadir') / meson.project_name()
moduledir = pkgdatadir / 'helloworldgnome4python'
gnome = import('gnome')

gnome.compile_resources('helloworldgnome4python',
  'helloworldgnome4python.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').full_path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', get_option('prefix') / get_option('localedir'))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'helloworldgnome4python.in',
  output: 'helloworldgnome4python',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir'),
  install_mode: 'r-xr-xr-x'
)

helloworldgnome4python_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

install_data(helloworldgnome4python_sources, install_dir: moduledir)
