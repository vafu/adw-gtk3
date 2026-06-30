root_dir        = join_paths(get_option('datadir'), 'themes')
theme_dir       = join_paths(root_dir, meson.project_name())
theme_dir_dark  = join_paths(root_dir, meson.project_name() + '-dark')
theme_dir_light_frosted = join_paths(root_dir, meson.project_name() + '-light-frosted')
theme_dir_dark_frosted  = join_paths(root_dir, meson.project_name() + '-dark-frosted')
# GTK3
gtk3_dir        = join_paths(theme_dir, 'gtk-3.0')
gtk3_dir_dark   = join_paths(theme_dir_dark, 'gtk-3.0')
gtk3_dir_light_frosted = join_paths(theme_dir_light_frosted, 'gtk-3.0')
gtk3_dir_dark_frosted  = join_paths(theme_dir_dark_frosted, 'gtk-3.0')
# GTK4
gtk4_dir        = join_paths(theme_dir, 'gtk-4.0')
gtk4_dir_dark   = join_paths(theme_dir_dark, 'gtk-4.0')
gtk4_dir_light_frosted = join_paths(theme_dir_light_frosted, 'gtk-4.0')
gtk4_dir_dark_frosted  = join_paths(theme_dir_dark_frosted, 'gtk-4.0')

sass = find_program('sass')

install_data('accent-color.css', install_dir: root_dir)

# Files can't have the same names in the build dir, so I need to put the meson junk in 2 dirs
subdir('theme-light')
subdir('theme-dark')
subdir('theme-light-frosted')
subdir('theme-dark-frosted')
