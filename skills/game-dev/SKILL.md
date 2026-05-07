---
name: game-dev
description: "Full-stack game development AI covering 13 specialist skills across 2D/3D games, Unity, game design, art direction, audio, multiplayer networking, mobile, PC/console, web browser games, VR/AR, and Minecraft plugin development. Use for Unity C# scripting, game loop design, sprite systems, tilemaps, physics, 3D rendering, shaders, HDRP/URP, GDD documents, player psychology, core loop design, balancing, asset pipeline, sound design, adaptive audio, multiplayer architecture, mobile touch input, iOS/Android deployment, web games with Phaser and WebGPU, VR/AR development, and Bukkit/Spigot/Paper Minecraft plugins. Trigger keywords: game, Unity, Godot, Unreal, 2D, 3D, sprite, tilemap, shader, HDRP, URP, game design, GDD, player psychology, core loop, balancing, game art, pixel art, animation, sound design, FMOD, Wwise, multiplayer, netcode, rollback, mobile game, touch input, iOS game, Android game, web game, Phaser, WebGPU, VR, AR, Quest, XR, Minecraft, Bukkit, Spigot, Paper, plugin."
metadata:
  version: 1.0.0
  source: _Master_Library/Game Development
---

# Game Dev

A complete, modular game development AI covering the full game creation lifecycle — from design and art direction to platform-specific engineering, multiplayer networking, and audio.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 🎮 Platform / Target
| Target | Load |
|--------|------|
| Web browser (HTML5, WebGL, Phaser, Three.js, WebGPU) | `web-games` |
| Mobile (iOS, Android — Unity, Godot, or native) | `mobile-games` |
| PC or console (Steam, desktop, Xbox, PlayStation) | `pc-games` |
| VR or AR headsets (Quest, PCVR, ARKit, ARCore) | `vr-ar` |

### 🔷 Dimension
| Dimension | Load |
|-----------|------|
| 2D game — sprites, tilemaps, physics, camera, animation | `2d-games` |
| 3D game — rendering pipeline, shaders, cameras, physics, LOD | `3d-games` |

### 🛠️ Engine
| Engine/Platform | Load |
|----------------|------|
| Unity (C#, URP/HDRP, cross-platform deployment, multi-agent orchestration) | `unity-developer` |
| Minecraft server plugin (Bukkit, Spigot, Paper, Brigadier commands) | `minecraft-bukkit-pro` |

### 🎨 Design & Creative
| Task | Load |
|------|------|
| Game Design Document (GDD), core loop design, player psychology, balancing | `game-design` |
| Art style selection, asset pipeline, sprite sheets, animation workflow | `game-art` |
| Sound design, music integration, adaptive audio, FMOD/Wwise | `game-audio` |

### 🌐 Multiplayer
| Task | Load |
|------|------|
| Multiplayer architecture, netcode, synchronization, lag compensation | `multiplayer` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
game-dev/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Universal Game Dev Standards

**Fun first** — Every technical decision serves the player experience. If optimization kills the feel, find a different optimization.

**Profile before optimizing** — Never guess at bottlenecks. CPU/GPU profilers tell the truth; intuition doesn't.

**Design the 30-second loop first** — If the core loop isn't fun in 30 seconds, no amount of content will save it.

**Playtest relentlessly** — You are not your player. Watch real people play without helping them.

**Scope ruthlessly** — Finished small game > unfinished ambitious game. Cut features, not quality.

**Data-driven balancing** — Instrument everything. Session length, death locations, level completion rates — data reveals what feels unfair.
