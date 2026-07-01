# Configure our index.theme file
dark_frosted_conf_data = configuration_data()
dark_frosted_conf_data.set('ThemeName', meson.project_name())
dark_frosted_conf_data.set('VariantThemeName', meson.project_name() + '-dark-frosted')
configure_file(input: '../index.theme.in', output: 'index.theme.dark-frosted', configuration: dark_frosted_conf_data)
install_data(meson.current_build_dir() / 'index.theme.dark-frosted', install_dir: theme_dir_dark_frosted, rename: 'index.theme')

# Make sure we have depend files so ninja can detect changes
sass_path = '../sass'
sass_depend_files = run_command(
  'find',
  sass_path,
  '-name', '*.scss',
  check : true
).stdout().split()

# Compile the CSS
gtk_dark_frosted_css_target = custom_target('generate_gtk_dark_frosted_css',
  input: '../sass/gtk-dark-frosted.scss',
  output: 'gtk.css',
  command: [sass,  '@INPUT@', '@OUTPUT@'],
  build_by_default: true,
  install: true,
  install_dir: gtk3_dir_dark_frosted,
  depend_files: sass_depend_files
)

gtk_dark_frosted_dark_css_target = custom_target('generate_gtk_dark_frosted_dark_css',
  input: '../sass/gtk-dark-frosted.scss',
  output: 'gtk-dark.css',
  command: [sass,  '@INPUT@', '@OUTPUT@'],
  build_by_default: true,
  install: true,
  install_dir: gtk3_dir_dark_frosted,
  depend_files: sass_depend_files
)

# GTK4

gtk4_asset_dir_dark_frosted = join_paths(gtk4_dir_dark_frosted, 'assets')

gtk4_assets_dark_frosted = [
  '../assets/bullet-symbolic.svg',
  '../assets/bullet-symbolic.symbolic.png',
  '../assets/bullet@2-symbolic.symbolic.png',
  '../assets/check-symbolic.svg',
  '../assets/check-symbolic.symbolic.png',
  '../assets/check@2-symbolic.symbolic.png',
  '../assets/dash-symbolic.svg',
  '../assets/dash-symbolic.symbolic.png',
  '../assets/dash@2-symbolic.symbolic.png',
  '../assets/devel-symbolic.svg',
]

gtk4_css_dark_frosted = [
  '../theme-dark/gtk4/gtk.css',
  '../theme-dark/gtk4/gtk-dark.css',
  '../theme-dark/gtk4/libadwaita.css',
]

libadwaita_tweaks_dark_frosted_target = custom_target('generate_libadwaita_tweaks_dark_frosted_css',
  input: '../sass/gtk4/theme-dark-frosted.scss',
  output: 'libadwaita-tweaks.css',
  command: [sass,  '@INPUT@', '@OUTPUT@'],
  build_by_default: true,
  install: true,
  install_dir: gtk4_dir_dark_frosted,
  depend_files: sass_depend_files
)

gtk_dark_frosted_theme_target = custom_target('generate_gtk_dark_frosted_theme',
  input: '../sass/gtk4/gtk4-dark-frosted.scss',
  output: 'gtk4.css',
  command: [sass,  '@INPUT@', '@OUTPUT@'],
  build_by_default: true,
  install: true,
  install_dir: gtk4_dir_dark_frosted,
  depend_files: sass_depend_files
)

install_data(gtk4_css_dark_frosted, install_dir: gtk4_dir_dark_frosted)
install_data(gtk4_assets_dark_frosted, install_dir: gtk4_asset_dir_dark_frosted)

# Misc
install_subdir('../assets', install_dir : gtk3_dir_dark_frosted, strip_directory : false)
install_data(['../theme-dark/thumbnail-dark.png'], install_dir: gtk3_dir_dark_frosted, rename: ['thumbnail.png'])
install_symlink('accent-color.css', install_dir:gtk3_dir_dark_frosted, pointing_to: '../../accent-color.css')
install_symlink('accent-color.css', install_dir:gtk4_dir_dark_frosted, pointing_to: '../../accent-color.css')
