# Omarchy Giants Theme

Standing on the shoulders of giants. A warm, low-contrast dark theme for
[Omarchy](https://omarchy.org) built around ink on aged paper: sepia and cream
foregrounds over a soft brown-black background, with a dusty terracotta accent.

This is for the original creators who made foundational contributions to computer science.
(We'll do another series for Internet and later).

![Giants preview](preview.jpg)

> **This fork** of [dhh/omarchy-giants-theme](https://github.com/dhh/omarchy-giants-theme)
> adds a glass look: a translucent bar, menus and notifications with the
> wallpaper blurred behind them, see-through windows, a soft shadow, and thin
> hairline borders. See [Glass](#glass) below.

## Wallpapers

Ten portraits of the giants everything since was built on, drawn as ink on
aged paper with technical diagrams of their contributions. Click any one for the
full 6144×4096 wallpaper.

<table>
<tr><td width="50%" align="center"><a href="backgrounds/1-turing-von-neumann.jpg"><img src="thumbnails/1-turing-von-neumann.jpg" alt="Alan Turing and John von Neumann"></a><br><strong>Alan Turing and John von Neumann</strong><br><sub>computability and the stored-program computer</sub></td><td width="50%" align="center"><a href="backgrounds/2-grace-hopper.jpg"><img src="thumbnails/2-grace-hopper.jpg" alt="Grace Hopper"></a><br><strong>Grace Hopper</strong><br><sub>compilers and COBOL</sub></td></tr>
<tr><td width="50%" align="center"><a href="backgrounds/3-john-backus.jpg"><img src="thumbnails/3-john-backus.jpg" alt="John Backus"></a><br><strong>John Backus</strong><br><sub>FORTRAN, BNF, and compilers</sub></td><td width="50%" align="center"><a href="backgrounds/4-edsger-dijkstra.jpg"><img src="thumbnails/4-edsger-dijkstra.jpg" alt="Edsger Dijkstra"></a><br><strong>Edsger Dijkstra</strong><br><sub>structured programming and algorithms</sub></td></tr>
<tr><td width="50%" align="center"><a href="backgrounds/5-tony-hoare.jpg"><img src="thumbnails/5-tony-hoare.jpg" alt="C. A. R. Hoare"></a><br><strong>C. A. R. Hoare</strong><br><sub>program verification and Hoare logic</sub></td><td width="50%" align="center"><a href="backgrounds/6-donald-knuth.jpg"><img src="thumbnails/6-donald-knuth.jpg" alt="Donald Knuth"></a><br><strong>Donald Knuth</strong><br><sub>algorithms, TeX, and technical publishing</sub></td></tr>
<tr><td width="50%" align="center"><a href="backgrounds/7-ken-thompson.jpg"><img src="thumbnails/7-ken-thompson.jpg" alt="Ken Thompson"></a><br><strong>Ken Thompson</strong><br><sub>Unix and operating systems</sub></td><td width="50%" align="center"><a href="backgrounds/8-dennis-ritchie.jpg"><img src="thumbnails/8-dennis-ritchie.jpg" alt="Dennis Ritchie"></a><br><strong>Dennis Ritchie</strong><br><sub>C and Unix</sub></td></tr>
<tr><td width="50%" align="center"><a href="backgrounds/9-barbara-liskov.jpg"><img src="thumbnails/9-barbara-liskov.jpg" alt="Barbara Liskov"></a><br><strong>Barbara Liskov</strong><br><sub>data abstraction and distributed systems</sub></td><td width="50%" align="center"><a href="backgrounds/10-adleman-rivest-shamir.jpg"><img src="thumbnails/10-adleman-rivest-shamir.jpg" alt="Adleman · Rivest · Shamir"></a><br><strong>Adleman · Rivest · Shamir</strong><br><sub>RSA public-key cryptography</sub></td></tr>
</table>

Research notes, source portrait credits, licenses, and generation details are in
[CREDITS.md](CREDITS.md).

## Install

Omarchy will not load `*.lua` or a terminal config from a theme installed with
`omarchy theme install`, because those files run code and a cloned theme comes
from someone else. It drops them and prints what it skipped. To get the full
glass look, clone your own working copy and link it into the themes folder:

```bash
git clone https://github.com/murilo-preto/omarchy-giants-theme.git ~/Github/omarchy-giants-theme
ln -s ~/Github/omarchy-giants-theme ~/.config/omarchy/themes/giants
omarchy theme set giants
```

`omarchy theme install https://github.com/murilo-preto/omarchy-giants-theme`
still works, but you only get what `shell.toml` provides: a translucent bar and
menus with nothing blurred behind them, so they look see-through rather than
frosted.

To pull in upstream changes (new wallpapers, palette fixes):

```bash
git remote add upstream https://github.com/dhh/omarchy-giants-theme.git  # once
git pull upstream main
```

## Glass

Ported from [omarchy-minimal-black](https://github.com/murilo-preto/omarchy-minimal-black),
recolored with the Giants palette.

| File | Purpose |
| --- | --- |
| `hyprland.lua` | Blur, soft shadow, 14px rounding, 1px translucent cream borders, window opacity, and a layer rule that blurs behind the bar, menus, notifications and popups |
| `shell.toml` | Omarchy's generated Giants shell colors with lower alphas: bar `0.55`, cards `0.70`, hairline borders at `0.15` |
| `alacritty.toml` | Terminal palette + `[window] opacity = 0.85` |

The window and terminal alphas compound. Alacritty's `0.85` applies to its
background, and the Hyprland window rule's `0.94` applies to the whole window.
The terminal background ends up near `0.80`, while text stays at `0.94`.

The layer rule's `ignore_alpha = 0.4` sits between the full-screen scrims
(<= 0.30) and the cards (>= 0.55). Opening a menu therefore blurs only what is
behind the card, not the whole screen. Keep that ordering if you tune the alphas.

Shipping `alacritty.toml` means Omarchy skips its template for this theme, so the
palette there is a hand copy of `colors.toml`. Keep the two in sync.

## Palette

| Role | Hex |
| --- | --- |
| Background | `#27241f` |
| Dark background | `#1d1b17` |
| Darker background | `#141210` |
| Lighter background | `#3d3a35` |
| Foreground | `#E1D5C2` |
| Accent | `#97786d` |
| Selection | `#4f4840` |
| Muted | `#8a857a` |

Full ANSI palette in [`colors.toml`](colors.toml). Icons are `Yaru-wartybrown`.
