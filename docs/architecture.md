# Architecture

This document describes the architecture visible in the private production repository without reproducing its source.

## Runtime structure

Godot scenes own screen-specific UI and interaction. Autoload singletons hold cross-scene services and persistent state. Small data and system classes isolate drink construction, order generation, validation, level configuration, special rules, and tutorial steps.

| Area | Responsibility |
|---|---|
| Scene controllers | Main menu, chapter/level selection, gameplay, results, shop, and settings |
| Game manager | Global run state, mode selection, level context, and achievement checks |
| Level context | Current level goals, rule set, timers, mistakes, and progress |
| Order pipeline | Generate valid orders, collect player selections, and compare results |
| Special-rule handler | Apply memory, rush, reverse, no-reset, VIP, and combined rules |
| Score manager | Base score, speed bonus, combo multiplier, attempt penalty, and coins |
| Save manager | Long-term progression and resumable endless-session JSON data |
| Locale service | Traditional Chinese, English, and Japanese strings and names |
| Platform services | Game Center, REST leaderboard, ads/consent, and purchases |

## Design observations

- Level data is defined separately from runtime UI, which supports a large content set without one scene per level.
- Level and endless modes share the gameplay screen and branch through an explicit level context.
- Rules can be combined, which avoids a separate implementation for every challenge permutation.
- Signals and manager boundaries coordinate UI, scoring, achievements, ads, and platform callbacks.
- The mobile viewport and touch sizing are deliberate project-level constraints.

## Public boundary

Service URLs, keys, ad identifiers, product identifiers, export settings, signing data, production scripts, and art/audio/font files are outside this showcase.

