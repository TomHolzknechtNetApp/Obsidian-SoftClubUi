# Obsidian-SoftClubUi

A CSS snippet that applies the Soft Club UI design system to Obsidian. You set all options in the Style Settings plugin.

> **Origin.** The design comes from [Soft Club UI](https://github.com/cobanov/soft-club-ui) by Mert Cobanov (MIT license). This repository is an independent port for Obsidian. The Soft Club UI project does not maintain it.

## Contents

- [About the port](#about-the-port)
- [Requirements](#requirements)
- [Files](#files)
- [Install the snippet](#install-the-snippet)
- [Install Style Settings](#install-style-settings)
- [Configure the snippet](#configure-the-snippet)
- [Import a preset](#import-a-preset)
- [Export your settings](#export-your-settings)
- [Settings reference](#settings-reference)
- [Palettes](#palettes)
- [Component mapping](#component-mapping)
- [How the snippet works with Style Settings](#how-the-snippet-works-with-style-settings)
- [Limits](#limits)
- [Remove the snippet](#remove-the-snippet)
- [License and credits](#license-and-credits)

## About the port

Soft Club UI is a React component library. Its style uses dark glass, phosphor green, cold blue, thin technical borders, low radii, and CRT scanlines.

This snippet takes the design values and the component styles from these files of the Soft Club UI repository:

| Soft Club UI file | Content used in the snippet |
| --- | --- |
| `packages/tokens/src/soft-club.css` | Colors, fonts, radii, shadows, motion, and the four palettes |
| `packages/ui/src/styles.css` | Component styles (Button, Card, Badge, Tabs, Alert, and others) |
| `apps/docs/src/index.css` | Page backdrop and scanline overlay |

The snippet applies these values to Obsidian elements. It contains no React code and no JavaScript.

## Requirements

| Item | Requirement |
| --- | --- |
| Obsidian | Desktop app. The author has not tested the mobile apps. See [Limits](#limits). |
| Rendering engine | Chromium 112 or later. The snippet uses CSS nesting and `color-mix()`. |
| Plugin | [Style Settings](https://github.com/community-archive/obsidian-style-settings). The author developed the snippet with version 1.0.9. |
| Color scheme | Dark. To use the snippet in light mode, turn on **Also apply in light mode**. |
| Network | Optional. Obsidian connects to `fonts.gstatic.com` to load Space Grotesk and JetBrains Mono. |

To see the Chromium version of your Obsidian app, do these steps:

1. Open the developer tools. On macOS, push <kbd>Cmd</kbd>+<kbd>Option</kbd>+<kbd>I</kbd>. On Windows and Linux, push <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd>.
2. Click the **Console** tab.
3. Type `process.versions.chrome` and push <kbd>Enter</kbd>.

If Style Settings is not installed, the snippet applies only the colors and the fonts of the green palette. The component styles stay off.

## Files

You need only one file.

| File | Required | Content |
| --- | --- | --- |
| `soft-club-ui.css` | Yes | The snippet. It contains all styles and the Style Settings definitions. |
| `presets/night-city.json` | No | An example preset: Night City palette, light mode on. |
| `LICENSE` | No | The MIT license for this port and for Soft Club UI. |

## Install the snippet

1. Download [`soft-club-ui.css`](soft-club-ui.css) from this repository.
2. In Obsidian, open **Settings > Appearance**.
3. Below **CSS snippets**, click the folder icon (**Open snippets folder**).
4. Copy `soft-club-ui.css` into this folder.
5. In Obsidian, click the reload icon (**Reload snippets**) next to the folder icon.
6. Turn on the toggle for **soft-club-ui**.
7. Below **Base color scheme**, select **Dark**.

The snippets folder is `<your vault>/.obsidian/snippets/`. If the folder does not exist, make the folder. If your vault uses a different configuration folder, use that folder instead of `.obsidian`.

## Install Style Settings

1. Open **Settings > Community plugins**.
2. If Restricted mode is on, click **Turn on community plugins**.
3. Click **Browse**.
4. Search for **Style Settings**.
5. Click **Install**.
6. Click **Enable**.

## Configure the snippet

1. Open **Settings > Style Settings**.
2. Click the heading **Soft Club UI** to expand the section.
3. Below **Palette**, select a palette.
4. Change other settings as necessary.

Obsidian applies each change immediately. If the Obsidian language is German, Style Settings shows German titles and descriptions.

The command **Style Settings: Toggle Disable Soft Club UI** turns the snippet off and on. You can assign a hotkey to this command in **Settings > Hotkeys**.

## Import a preset

A preset is a JSON file with Style Settings values.

> [!CAUTION]
> The import replaces the current values of all settings in the file. It does not change the settings of other themes or snippets.

1. Open **Settings > Style Settings**.
2. At the top of the page, click **Import**.
3. Click **Import from file**.
4. Select the file `presets/night-city.json`.

You can also paste the JSON text into the text field and click **Save**.

## Export your settings

1. Open **Settings > Style Settings**.
2. In the heading **Soft Club UI**, click the export icon (tooltip **Export settings**).
3. Click **Copy to clipboard**.

The JSON text contains only the values that you changed. You can share the text as a preset.

## Settings reference

The ID of a toggle or a dropdown option is the CSS class that Style Settings adds to `body`. The ID of a color, a slider, or a text field is a CSS variable (`--ID`).

### General

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Disable Soft Club UI | `sc-off` | Toggle | Off | Turns off the full snippet. The snippet stays enabled in Appearance. |
| Also apply in light mode | `sc-everywhere` | Toggle | Off | Applies the snippet also in light mode. |

### Palette

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Palette | `sc-palette` | Dropdown | Green | Selects one of the four Soft Club UI palettes. See [Palettes](#palettes). |
| Hover accent | `sc-hover` | Dropdown | Warm | Sets the tint of hovered items: Warm, Primary, or Neutral. |

### Colors (override palette)

Each color picker overrides the value of the selected palette. To go back to the palette value, click the reset arrow of the setting.

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Background | `sc-bg` | Color | `#050706` | Background of notes and the editor. |
| Background soft | `sc-bg-soft` | Color | `#0a1110` | Sidebars, ribbon, title bar. |
| Glass surface | `sc-surface-color` | Color | `#0d1613` | Base color of cards and code blocks (used at 74% opacity). |
| Raised glass surface | `sc-raised-color` | Color | `#192a24` | Menus, modals, popovers (used at 78% opacity). |
| Inset surface | `sc-inset-color` | Color | `#040908` | Inline code, form fields. |
| Text | `sc-text` | Color | `#eef6ee` | Normal text. |
| Text muted | `sc-text-muted` | Color | `#a9b9ae` | Secondary text, icons. |
| Text subtle | `sc-text-subtle` | Color | `#74867b` | Labels, table headers, status bar. |
| Primary accent | `sc-primary` | Color | `#8effad` | Soft Club "accent green". Links, active tab, checkboxes, CTA buttons. |
| Secondary accent | `sc-secondary` | Color | `#8bb8d7` | Soft Club "accent blue". External links, tags, keywords. |
| Warm (hover tint) | `sc-warm` | Color | `#ff8a3d` | Background tint of hovered items. |
| Warning | `sc-warning` | Color | `#ff8a3d` | Text color on hover, numbers in code. |
| Danger | `sc-danger` | Color | `#f06a54` | Warning buttons, errors. |
| Panel tint | `sc-panel` | Color | `#e1ffed` | Light tint for faint fills on outline buttons, tables, and keys. |
| Border color | `sc-border-color` | Color | `#aeffd2` | Base color of all borders. |
| Border strength | `sc-border-alpha` | Slider | 24% | Opacity of normal borders. |
| Strong border strength | `sc-border-strong-alpha` | Slider | 46% | Opacity of borders on modals, menus, outline buttons, and hovered fields. |

### Typography

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Sans font | `sc-font-sans` | Text | Space Grotesk | Font of text and interface. The fallback is Helvetica. |
| Mono font | `sc-font-mono` | Text | JetBrains Mono | Font of code, tags, labels, and the status bar. |
| Override fonts set in Appearance | `sc-force-fonts` | Toggle | On | Uses the Soft Club fonts also when **Settings > Appearance** sets a custom font. |
| H6 as mono "kicker" label | `sc-h6-kicker` | Toggle | On | Shows H6 headings as small green mono labels, like the GlassPanel kicker. |
| H1 and note title as gradient text | `sc-h1-gradient` | Toggle | Off | Shows a gradient from text to primary to secondary color (GradientText component). |
| Mono status bar | `sc-mono-statusbar` | Toggle | On | Shows the status bar in the mono font. |

### Shape and glass

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Radius small | `sc-radius-1` | Slider | 2px | Tags, checkboxes, keys, menu items. |
| Radius medium | `sc-radius-2` | Slider | 4px | Buttons, fields, callouts, tables. |
| Radius large | `sc-radius-3` | Slider | 6px | Cards, modals, menus, code blocks. |
| Glass blur | `sc-glass-blur` | Slider | 18px | Blur behind modals, menus, and popovers. |

### Atmosphere

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Editor backdrop | `sc-backdrop` | Toggle | On | Shows a technical grid and a soft glow behind notes. |
| Backdrop grid row height | `sc-grid-size` | Slider | 24px | Row height of the grid. The column width is four times this value. |
| CRT scanline overlay | `sc-scanlines` | Toggle | On | Shows fine horizontal lines over the full window. |
| Scanline overlay intensity | `sc-scanline-opacity` | Slider | 0.28 | Opacity of the scanline overlay. |
| Scanlines on glass surfaces | `sc-surface-scanlines` | Toggle | On | Shows scanlines on modals, menus, popovers, notices, and code blocks. |

### Components

| Setting | ID | Type | Default | Function |
| --- | --- | --- | --- | --- |
| Glass surfaces | `sc-mod-glass` | Toggle | On | Modals, command palette, menus, popovers, suggestions, notices, tooltips. |
| Buttons | `sc-mod-buttons` | Toggle | On | Default, call-to-action, and warning buttons. |
| Switches | `sc-mod-switches` | Toggle | On | Toggles in the settings, in the style of the Soft Club Switch. |
| Tabs | `sc-mod-tabs` | Toggle | On | Flat tabs with a primary underline on the active tab. |
| Active file marker | `sc-mod-nav` | Toggle | On | Primary edge on the active file and on the active settings tab. |
| Tags as badges | `sc-mod-tags` | Toggle | On | Tags in mono font, in uppercase, with a border. |
| Callouts as alerts | `sc-mod-callouts` | Toggle | On | Neutral border, scanline fill, and a colored data line at the bottom. |
| Animate callout data line | `sc-callout-motion` | Toggle | On | Moves the data line. The animation stops when the system setting "reduce motion" is on. |
| Code blocks as console | `sc-mod-code` | Toggle | On | Glass frame with a console bar that shows the language (Reading view). |
| Tables | `sc-mod-tables` | Toggle | On | Mono uppercase headers, row lines only, warm tint on hovered rows. |
| Properties as glass panel | `sc-mod-properties` | Toggle | On | Shows the properties of a note in a glass panel with mono labels. |
| Kbd, separator, progress bar | `sc-mod-misc` | Toggle | On | Styles for `<kbd>`, horizontal rules, and `<progress>`. |

## Palettes

The palettes are the four themes of Soft Club UI.

| Palette | Class | Background | Primary | Secondary | Warm |
| --- | --- | --- | --- | --- | --- |
| Green (default) | `sc-palette-green` | `#050706` | `#8effad` | `#8bb8d7` | `#ff8a3d` |
| Blue | `sc-palette-blue` | `#04070d` | `#87f2e6` | `#7ebcff` | `#ffd16a` |
| Orange | `sc-palette-orange` | `#0b0300` | `#ff9a20` | `#ffd27a` | `#ffcf35` |
| Night City | `sc-palette-night-city` | `#171019` | `#a1eae3` | `#5eb3af` | `#d22348` |

## Component mapping

| Soft Club UI component | Obsidian element |
| --- | --- |
| Design tokens | Obsidian CSS variables: backgrounds, text, accent, borders, radii, fonts, code colors, graph colors |
| Page backdrop | Background of Markdown views: grid and glow |
| Scanline overlay | Overlay on the full window |
| Card, GlassPanel, Dialog, Dropdown Menu, Popover, Toast | Modals, command palette, menus, hover previews, suggestions, notices |
| Tooltip | Tooltips |
| Button | Buttons: default, `mod-cta`, `mod-warning` |
| Input, Checkbox, Native Select | Text fields, dropdowns, task checkboxes |
| Switch | Toggles in the settings |
| Tabs | Workspace tabs, settings tabs, active file |
| Badge | Tags |
| Alert | Callouts |
| MockConsole | Code blocks |
| Table, Kbd, Separator, Progress, ScrollArea | Tables, `<kbd>`, horizontal rules, `<progress>`, scroll bars |
| GlassPanel kicker, GradientText | H6 headings, H1 headings and note title |

The snippet does not include the animated canvas and ASCII components, for example AsciiHero, MatrixRain, and ParticleField. It also does not include charts and interactive widgets. These components need JavaScript. A CSS snippet cannot add them.

## How the snippet works with Style Settings

This section is for theme and snippet authors. The snippet follows the [Style Settings documentation](https://github.com/community-archive/obsidian-style-settings).

- The settings are in a `/* @settings */` comment with the properties `name`, `id`, and `settings`. The section ID is `soft-club-ui`.
- Each setting has a `title.de` and a `description.de` for German.
- The toggle `sc-off` has `addCommand: true`. Style Settings adds a command for this toggle.
- The snippet declares the editable variables (`--sc-*`) on `body`. Style Settings writes changed values to `body.css-settings-manager`. That selector has a higher specificity, so the values of the user win.
- The palettes use `body:where(.sc-palette-blue)` and similar selectors. The specificity stays equal to `body`. Thus a color picker can override a palette value.
- The snippet sets the Obsidian variables and the component rules in one scope: `body:is(.theme-dark, .sc-everywhere):not(.sc-off)`. This scope has a higher specificity than theme rules such as `.theme-dark`.

## Limits

- The console bar on code blocks shows only in Reading view. In Live Preview, code blocks get only the token colors.
- The console bar shows the CSS class of the code block, for example `language-python`.
- In Live Preview, tags also show in uppercase. The text in the file does not change.
- If a font is not installed on the computer, Obsidian loads the font from Google Fonts. To prevent this connection, install Space Grotesk and JetBrains Mono, or change **Sans font** and **Mono font**.
- The author developed the snippet on Obsidian desktop for macOS with the Things theme. The author has not tested the mobile apps.
- The snippet overrides the colors of the active theme. If a theme uses fixed colors for an element, that element keeps the theme colors.

## Remove the snippet

Style Settings keeps your values after you remove the snippet. After the removal, Style Settings does not show the section **Soft Club UI**. Thus, if you want to delete your values, do steps 1 and 2 first.

1. Optional: open **Settings > Style Settings**.
2. Optional: in the heading **Soft Club UI**, click the reset icon (tooltip **Reset all settings to default**).
3. Open **Settings > Appearance**.
4. Below **CSS snippets**, turn off the toggle for **soft-club-ui**.
5. Optional: delete `soft-club-ui.css` from the snippets folder.

## License and credits

This port is available under the MIT license. See [LICENSE](LICENSE).

| Part | Author | License |
| --- | --- | --- |
| Soft Club UI design system (design values, component styles) | [Mert Cobanov](https://github.com/cobanov/soft-club-ui) | MIT |
| Obsidian port (this snippet) | Tom Holzknecht | MIT |
| Style Settings plugin (not included) | [mgmeyers and contributors](https://github.com/community-archive/obsidian-style-settings) | GPL-3.0 |
| Space Grotesk, JetBrains Mono (not included, loaded from Google Fonts) | Florian Karsten, JetBrains | SIL Open Font License 1.1 |
