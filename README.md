# Reds Not Dead

A red-and-black Omarchy theme built around true black surfaces, vivid red accents, and white highlights.

## Design

- True black base: `#000000`
- Primary red: `#F60101`
- Bright red: `#ff0000`
- Dark red depth: `#4d0000` and `#800000`
- White for readable foregrounds and high-contrast accents
- No pink, orange, cyan, green, navy, or purple theme drift

## Installation

Install the theme using Omarchy's theme installer:

```bash
omarchy theme install https://github.com/NotProniss/reds-not-dead
```

Then apply it:

```bash
OMARCHY_PATH=/usr/share/omarchy omarchy theme set reds-not-dead
```

The theme contains safe, theme-scoped Omarchy files such as:

- `colors.toml`
- `shell.toml`
- `icons.theme`
- backgrounds and preview assets

## Palette

The active-window border is defined portably in `colors.toml`:

```toml
hyprland_active_border = "rgba(F60101ee) rgba(4d0000ee) 45deg"
```

This is consumed by Omarchy's generated Hyprland template and does not require Lua.

Terminal emulator configuration and Starship configuration are intentionally not included. Users keep their own terminal settings.

## Optional Kanada icon theme

Reds Not Dead bundles the unchanged `KanadaIcons` icon theme. It is installed separately because GTK icon themes must live in the user's icon search path.

After applying Reds Not Dead, install the bundled icon theme with:

```bash
mkdir -p ~/.local/share/icons
cp -a ~/.local/state/omarchy/current/theme/icons/KanadaIcons ~/.local/share/icons/KanadaIcons
gsettings set org.gnome.desktop.interface icon-theme 'KanadaIcons'
nautilus -q
```

The bundled icon files are unchanged from the upstream Kanada icon theme. Reds Not Dead does not modify or recolor its SVGs.

To install directly from upstream instead:

```bash
tmp=$(mktemp -d)
git clone --depth=1 https://github.com/nesuko82/kde-kanada.git "$tmp/kde-kanada"
mkdir -p ~/.local/share/icons
cp -a "$tmp/kde-kanada/icons" ~/.local/share/icons/KanadaIcons
gsettings set org.gnome.desktop.interface icon-theme 'KanadaIcons'
nautilus -q
```

To return to the previous icon theme:

```bash
gsettings set org.gnome.desktop.interface icon-theme 'Yaru-red'
nautilus -q
```

## Scope and limits

Reds Not Dead intentionally contains no Lua and no terminal-specific configuration. The theme's Hyprland border is supplied through `hyprland_active_border` in `colors.toml`, so it remains compatible with Omarchy's safe Git-installed theme flow.

Window rounding and other behavior changes are not included. The optional icon installation is separate from the Omarchy theme and only changes the selected icon theme.

## Credits and licenses

The optional icon theme comes from:

- [kde-kanada](https://github.com/nesuko82/kde-kanada) by nesuko82

KanadaIcons includes its own LGPLv3 license and Breeze/KDE Visual Design Group attribution. Preserve the icon component's `LICENSE` and `AUTHORS` files if redistributing the icon files directly.

## Status

Reds Not Dead is ready for use. The Omarchy palette, shell styling, portable active border, and optional icon instructions are included.
