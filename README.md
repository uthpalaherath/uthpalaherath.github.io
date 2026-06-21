# This is my homepage

Website: <https://uthpalaherath.com>

## Local Minimal Mistakes Overrides

This site uses the remote Minimal Mistakes theme from `_config.yml`, currently `mmistakes/minimal-mistakes@4.28.0`. Most theme files are loaded automatically from upstream. The files below intentionally override upstream theme files or add site-specific styles.

- `_sass/minimal-mistakes.scss`: imports the upstream Minimal Mistakes partials and adds the local `minimal-mistakes/custom` partial.
- `_sass/minimal-mistakes/_variables.scss`: customizes theme variables, including the wider page width, brand colors needed by upstream `4.28.0`, and existing color preferences.
- `_sass/minimal-mistakes/_archive.scss`: adds hover styling for archive items.
- `_sass/minimal-mistakes/_page.scss`: customizes hero text shadow styling.
- `_sass/minimal-mistakes/_sidebar.scss`: customizes sidebar opacity, author avatar size/border, author name weight, and author bio sizing.
- `_sass/minimal-mistakes/_custom.scss`: contains site-specific custom styles such as `.my-custom-notice`.
- `_layouts/single.html`: adds the subscription form include, hides page dates, and disables post pagination.
- `assets/css/main.scss`: imports the selected Minimal Mistakes skin/theme and adds responsive root font scaling plus video gallery styles.

When updating the remote theme version, compare these files against the matching upstream tag because local files shadow upstream versions.
