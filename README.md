# Synthwave Fluoromachine (Cursor/VS Code)
![Synthwave '84 logo over a cityscape](./banner.png)

This is a fork of Robb Owen's excellent [Synthwave '84 theme](https://github.com/robb0wen/synthwave-vscode), merged with the iconic [Fluoromachine](https://colorsublime.github.io/themes/FluoroMachine/) color palette, and enhanced with [Epic 80s Animations](https://github.com/thecodemonkey/synthwave-x-fluoromachine-epic-animations). The result is a neon-drenched coding environment that combines the best of multiple worlds: the modern infrastructure of Synthwave '84, the vibrant purple and cyan aesthetics of Fluoromachine, and smooth retro animations.

![Theme screenshot](https://repository-images.githubusercontent.com/184457193/69dcff00-14d2-11ea-90e1-4bdf6fef80ca)

__No external extensions needed!__ The glow effect is built-in and can be toggled on/off with simple commands.

## Features

- **Fluoromachine color palette**: Purple (#8a2dc0), cyan (#61e2ff), and hot pink (#fc199a) dominate the theme
- **Built-in neon glow**: Token-level text shadows create that authentic neon aesthetic
- **Epic 80s animations**: Hover effects, pulsing tooltips, animated cursors, and more
- **3D perspective grid**: Retro-futuristic grid effect at the bottom of your editor
- **Scanlines overlay**: Subtle CRT monitor effect for maximum nostalgia
- **Configurable brightness**: Adjust the glow intensity to your preference
- **Enhanced language support**: Go, Clojure, Python, C/C++, Elixir, Markdown, Dart, Scala, and more

## Installation

Install from the VS Marketplace (once published) or install locally:

```bash
cd synthwave-fluoromachine-cursor
code --install-extension synthwave-fluoromachine-cursor-0.2.0.vsix
```

## Enabling Neon Dreams

The theme works beautifully out of the box, but to enable the full neon glow effect:

### Prerequisites
- **Windows users**: You may need to run VS Code with administrator privileges
- **Linux/Mac users**: Ensure VS Code is not installed in a read-only location and you have write permissions

### Steps

1. Set your active color theme to **Synthwave Fluoromachine (Cursor/VS Code)**
2. Open your command palette with `Ctrl + Shift + P` or `Shift + ⌘ + P`
3. Choose "__Enable Neon Dreams__"
4. Restart VS Code when prompted

The neon glow should now be active!

### Customizing the Glow

#### Adjust brightness
In your `settings.json`, add:
```json
"synthwave84.brightness": 0.45
```
The value should be a float from 0 to 1, where 0.0 is fully transparent. The default is 0.45. After changing, rerun "__Enable Neon Dreams__" to apply.

#### Disable glow but keep chrome updates
In your `settings.json`, add:
```json
"synthwave84.disableGlow": true
```
Then rerun "__Enable Neon Dreams__" to apply.

### Disabling Neon Dreams

Open your command palette and choose "__Disable Neon Dreams__", then restart VS Code.

## Fixing the Corruption Warning

Because enabling the glow modifies core VS Code files, you may see a "corrupted" warning. You can safely dismiss this, or remove it entirely with the [Fix VSCode Checksums](https://marketplace.visualstudio.com/items?itemName=lehni.vscode-fix-checksums) extension.

After installing, run `Fix Checksums: Apply` from the command palette, then fully restart VS Code.

## Updates

Every time VS Code updates, you'll need to rerun "__Enable Neon Dreams__" to restore the glow effect.

## Font Recommendation

The theme works with any font, but for that authentic retro-futuristic look, try:
- [Operator Mono](https://github.com/kiliman/operator-mono-lig) (with ligatures)
- [Fira Code](https://github.com/tonsky/FiraCode) (with ligatures)
- [JetBrains Mono](https://www.jetbrains.com/lp/mono/)

The font being used in the screenshot above is Operator Mono with Ligatures.

## Credits

This theme builds on the work of amazing developers:

- **Robb Owen** (@robbowen) - Original [Synthwave '84 theme](https://github.com/robb0wen/synthwave-vscode)
- **fullerenedream** - Original [Fluoromachine color scheme](https://colorsublime.github.io/themes/FluoroMachine/)
- **Jeremy Laskar** (@webrender) - Original [Synthwave x Fluoromachine fork](https://github.com/webrender/synthwave-vscode-x-fluoromachine)
- **thecodemonkey** - [Epic 80s Animations](https://github.com/thecodemonkey/synthwave-x-fluoromachine-epic-animations)

Maintained by **Lucas Johnston Kurilov** (@lujstn)

## License

See LICENSE file for details.
