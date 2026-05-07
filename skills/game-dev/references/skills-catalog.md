# Game Dev — Skills Catalog

Full instructions for all sub-skills. Read the relevant section before executing any game development task.

---

## Table of Contents

**Dimension**
- [2d-games](#2d-games) — Sprites, tilemaps, physics, camera, animation
- [3d-games](#3d-games) — Rendering pipeline, shaders, physics, LOD, cameras

**Engine / Platform**
- [unity-developer](#unity-developer) — Unity 6 LTS, URP/HDRP, C#, cross-platform, 6-agent system
- [minecraft-bukkit-pro](#minecraft-bukkit-pro) — Bukkit/Spigot/Paper plugins, Brigadier, Paper API

**Platform Target**
- [web-games](#web-games) — Phaser, Three.js, WebGPU, PWA, browser optimization
- [mobile-games](#mobile-games) — Touch input, battery, iOS/Android, app stores
- [pc-games](#pc-games) — Engine selection, Steam, performance, platform features
- [vr-ar](#vr-ar) — Comfort guidelines, Quest/PCVR, ARKit/ARCore, XR interaction

**Design & Creative**
- [game-design](#game-design) — GDD, core loop, player psychology, balancing, progression
- [game-art](#game-art) — Art style selection, asset pipeline, animation workflow
- [game-audio](#game-audio) — Sound design, music integration, adaptive audio, FMOD/Wwise

**Multiplayer**
- [multiplayer](#multiplayer) — Architecture, netcode, synchronization, lag compensation

---

---

## 2d-games

**When to use:** Building 2D game systems — sprite management, tilemaps, 2D physics, camera systems, or 2D animation.

### Sprite Systems
- **Atlas/Sprite Sheet**: combine multiple sprites into one texture to reduce draw calls. Tool: TexturePacker, Aseprite export.
- **Animation**: frame sequences with playback speed; blend trees for smooth transitions between states
- **Batching**: group sprites sharing the same texture/material into a single draw call

### Tilemap Architecture
```
World → Chunks (16×16 or 32×32 tiles) → Tiles
├── Render layer (visual)
├── Collision layer (physics)
└── Data layer (triggers, spawn points, metadata)
```

- Chunk-based loading: only load chunks near the player — essential for large worlds
- Rule tiles: auto-tile based on neighbors (grass → dirt transition handled automatically)
- Z-ordering: sort sprites by Y position for top-down perspective depth

### 2D Physics
| Use Case | Approach |
|----------|----------|
| Platformer | Kinematic character controller (not rigidbody) for precise control |
| Top-down | Rigidbody2D with drag; or kinematic with manual movement |
| Puzzle | Static/Rigidbody2D, rely on physics engine |

- Avoid moving Rigidbody2D via Transform directly — use `MovePosition` / `velocity`
- Physics layers: assign collision layers to avoid unnecessary overlap checks

### Camera Systems
- Follow cam: lerp toward player position with configurable smoothing
- Camera bounds: clamp to world edges to prevent showing outside world
- Screen shake: perlin noise offset, decay over time (don't use additive random — too jarring)
- Cinemachine (Unity) or Camera2D (Godot) handle most complex cases

---

## 3d-games

**When to use:** Building 3D game systems — rendering pipeline setup, shaders, 3D physics, LOD, or camera rigs.

### Rendering Pipeline
```
Vertex Processing → Geometry shaders → Rasterization → Fragment/Pixel shaders → Post-processing
```

- **Forward rendering**: simpler, better for transparent objects, fewer lights
- **Deferred rendering**: handles many lights efficiently, no transparent object support without workarounds
- **URP (Unity)**: default choice for mobile/cross-platform; forward renderer, good performance
- **HDRP (Unity)**: high-end PC/console; physically-based, volumetrics, ray tracing

### Shader Fundamentals
```hlsl
// Basic vertex/fragment structure (HLSL/ShaderLab)
Shader "Custom/MyShader" {
    Properties { _Color("Color", Color) = (1,1,1,1) }
    SubShader {
        Pass {
            CGPROGRAM
            #pragma vertex vert
            #pragma fragment frag
            // vertex: transform positions to clip space
            // fragment: output per-pixel color
            ENDCG
        }
    }
}
```

- PBR (Physically Based Rendering): metallic/roughness workflow; use albedo, normal, metallic, roughness maps
- Shader Graph (Unity) / Visual Shader (Godot): node-based for non-programmers; compiles to HLSL

### Level of Detail (LOD)
- LOD0: full detail (< 10m from camera)
- LOD1: 50% poly reduction (10-30m)
- LOD2: 25% poly reduction (30-80m)
- Imposter: billboard texture (> 80m, distant trees/rocks)
- Auto-LOD tools: Simplygon, Unity LOD Group

### 3D Physics
- Mesh colliders: expensive — use primitive colliders (box, capsule, sphere) wherever possible
- Layer matrix: define which layers can collide; reduces physics checks
- Physics materials: restitution (bounciness) + friction per surface type

---

---

## unity-developer

**When to use:** Building with Unity — C# scripting, URP/HDRP setup, cross-platform deployment, performance optimization, or complex game systems.

### Core Principle
Build systems that let designers iterate fast. Expose parameters to the Inspector; don't hardcode gameplay values.

### Unity 6 LTS Key Features
- **Entities (DOTS)**: ECS architecture for performance-critical systems (thousands of enemies, particles)
- **Addressables**: async asset loading, reduces initial download size
- **URP/HDRP**: choose at project start — switching later is painful
- **UI Toolkit**: modern CSS-inspired UI system; prefer over legacy Canvas for complex UIs

### C# Patterns for Unity
```csharp
// Singleton (use sparingly — prefer dependency injection)
public class GameManager : MonoBehaviour {
    public static GameManager Instance { get; private set; }
    void Awake() {
        if (Instance != null) { Destroy(gameObject); return; }
        Instance = this;
        DontDestroyOnLoad(gameObject);
    }
}

// ScriptableObject for data (not MonoBehaviour)
[CreateAssetMenu(fileName = "EnemyData", menuName = "Game/Enemy Data")]
public class EnemyData : ScriptableObject {
    public float Health;
    public float Speed;
    public float AttackDamage;
}

// Object pooling (never Instantiate in hot path)
// Use Unity's ObjectPool<T> (Unity 2021+)
```

### Performance Rules
- **Avoid allocations in Update()**: no `new`, `LINQ`, string concatenation per frame
- **Cache component references**: `GetComponent<T>()` is expensive — cache in `Awake()`
- **Occlusion culling**: enable for indoor/complex scenes
- **Batching**: static batching for environment, GPU instancing for many identical objects
- **Profiler first**: never guess. Unity Profiler → CPU/GPU timelines → identify actual bottleneck

### Multi-Agent Orchestration (6-Agent System)
For large features, Unity-developer coordinates up to 6 specialized agents:
- **Gameplay Agent**: core mechanics, player controller
- **AI Agent**: enemy behavior, pathfinding, state machines
- **UI Agent**: HUD, menus, UI Toolkit
- **Audio Agent**: Wwise/FMOD integration, audio manager
- **Performance Agent**: profiling, optimization, memory
- **QA Agent**: testing, edge cases, platform compatibility

Run standups, track blockers, enforce quality gates before merge.

### Cross-Platform Deployment
| Platform | Key Settings |
|----------|-------------|
| iOS | IL2CPP backend, ARM64, Xcode signing |
| Android | Target API 33+, 64-bit only, App Bundle |
| WebGL | Compression (Brotli), memory size, no threads |
| PC | IL2CPP for release, IL for debug speed |

---

## minecraft-bukkit-pro

**When to use:** Building Minecraft server plugins — Paper/Spigot/Bukkit plugin development, command systems, event handling, or custom gameplay mechanics.

### Core Expertise
- **Event-driven architecture**: listener registration, event priorities (LOWEST → HIGHEST → MONITOR), custom events
- **Paper API**: Adventure library for text components, MiniMessage for formatting, Lifecycle API for modern registration
- **Brigadier commands**: type-safe command framework (replaces old CommandExecutor), tab completion, argument types
- **Inventory GUIs**: custom GUI systems, slot click handling, NBT manipulation

### Plugin Structure
```java
public class MyPlugin extends JavaPlugin {
    @Override
    public void onEnable() {
        // Register listeners
        getServer().getPluginManager().registerEvents(new MyListener(this), this);
        // Register commands (Paper lifecycle)
        getLifecycleManager().registerEventHandler(LifecycleEvents.COMMANDS, event -> {
            event.registrar().register(buildCommand());
        });
        getLogger().info("MyPlugin enabled!");
    }
}
```

### Event Handling Patterns
```java
@EventHandler(priority = EventPriority.NORMAL, ignoreCancelled = true)
public void onPlayerJoin(PlayerJoinEvent event) {
    Player player = event.getPlayer();
    // Always check ignoreCancelled = true for most handlers
    // Use MONITOR priority only for reading final state, never modify
}
```

### Performance Rules
- Avoid synchronous I/O on the main thread: use `Bukkit.getScheduler().runTaskAsynchronously()`
- Cache player data in memory during session; persist to DB async on logout
- Chunk operations: load chunks async before accessing block data
- NMS (net.minecraft.server): wrap in try/catch with version check; consider abstraction layers

---

---

## web-games

**When to use:** Building browser-based games using HTML5 canvas, WebGL, Phaser, Three.js, or WebGPU.

### Framework Selection
```
What type of game?
├── 2D game (sprites, tilemaps) → Phaser 3
├── 3D game → Three.js or Babylon.js
├── Simple canvas experiment → Vanilla Canvas API
├── High-performance 3D (modern browsers only) → WebGPU
└── Physics simulation → Matter.js (2D) or Rapier WASM (3D)
```

### Phaser 3 Essentials
```javascript
const game = new Phaser.Game({
    type: Phaser.AUTO, // WebGL with Canvas fallback
    width: 800,
    height: 600,
    physics: { default: 'arcade', arcade: { gravity: { y: 300 } } },
    scene: [PreloadScene, GameScene, UIScene]
});

// Scene lifecycle
class GameScene extends Phaser.Scene {
    preload() { this.load.spritesheet('player', 'player.png', { frameWidth: 32, frameHeight: 32 }); }
    create() { this.player = this.physics.add.sprite(100, 100, 'player'); }
    update() { /* game loop */ }
}
```

### Browser Optimization
- **Asset loading**: compress images (WebP), use texture atlases, implement loading screen
- **Game loop**: use `requestAnimationFrame` (built into Phaser/Three.js); cap at 60fps
- **Memory**: pool objects (bullets, enemies); never create objects in game loop
- **Mobile**: touch events alongside keyboard; scale to viewport with `Phaser.Scale.FIT`
- **PWA**: add `manifest.json` + service worker for offline play + "Add to Home Screen"

### WebGPU (Cutting Edge)
- Only for modern Chrome/Edge/Firefox Nightly — check `navigator.gpu` before using
- 10-50x faster than WebGL for compute-heavy workloads
- Fallback to WebGL2 for unsupported browsers

---

## mobile-games

**When to use:** Building mobile games with Unity, Godot, or native frameworks targeting iOS and Android.

### Platform Constraints (Design Around These)
| Constraint | Impact | Strategy |
|------------|--------|---------|
| Touch input | No precise mouse | Large hit areas (min 44×44pt), gestures |
| Battery | Players notice heat | Limit to 60fps (not 120), reduce GPU work in background |
| Memory | Crash = bad review | Stream assets, unload unused scenes |
| Network | Variable connectivity | Offline-first design, graceful degradation |
| Screen sizes | 5" to 13" tablets | Flexible layouts, percentage-based positioning |

### Touch Input Patterns
- Tap: immediate action (no delay)
- Hold: secondary action after 500ms
- Swipe: directional input with minimum distance threshold
- Pinch: zoom (pinch-to-zoom is a platform expectation, don't break it)
- Never require precise multi-finger gestures for core gameplay

### App Store Optimization (ASO)
- Title: primary keyword in first 30 characters
- Screenshots: first screenshot = most important. Show gameplay, not logos.
- Video preview: autoplay without sound — show the most exciting moment in first 3 seconds
- Ratings: prompt for review after positive moments (level complete, not during difficulty)

### Performance for Mobile
- Target 60fps on midrange devices (3-year-old flagship = midrange today)
- Compress textures: ASTC for iOS, ETC2 for Android, PVRTC for older iOS
- Draw call budget: < 100 for mobile (vs 1000+ for PC)
- Battery mode: reduce update rate when app is backgrounded

---

## pc-games

**When to use:** Building PC or console games — engine selection, platform-specific features, Steam integration, or PC-specific performance optimization.

### Engine Selection
```
What are you building?
├── 2D indie / solo dev → Godot 4 (free, lightweight, GDScript)
├── Cross-platform 3D → Unity (ecosystem, asset store, C#)
├── AAA / large team 3D → Unreal Engine (Blueprints + C++, best visuals)
├── Rust/performance-critical → Bevy (ECS, modern, growing ecosystem)
└── Web + desktop hybrid → Godot (exports to HTML5, PC, mobile)
```

### Steam Integration
- **Steamworks SDK**: achievements, leaderboards, cloud saves, DLC, Workshop
- **Steam Input**: controller abstraction layer — support Xbox, PlayStation, Switch, generic
- **Steam Deck**: verify game works in Deck Verified or Playable tier; test with controller and 800p
- **Workshop**: enable modding → dramatically extends game life

### PC Performance Targets
| Spec Tier | Target Frame Rate | GPU |
|-----------|-----------------|-----|
| Low-end | 30fps | GTX 1060 / RX 580 |
| Mid-range | 60fps | RTX 2070 / RX 5700 XT |
| High-end | 144fps | RTX 3080+ |

- Always include graphics presets (Low/Medium/High/Ultra)
- VSync toggle, frame rate cap option
- Resolution independence: support 1080p through 4K

---

## vr-ar

**When to use:** Building VR or AR experiences — comfort optimization, interaction design, platform deployment, or XR-specific patterns.

### VR Comfort — Non-Negotiable Rules
- **Frame rate**: 72fps minimum (Quest), 90fps recommended, 120fps for competitive. Missed frames = nausea.
- **Latency**: motion-to-photon < 20ms. Never throttle the render pipeline.
- **No acceleration without locomotion**: sudden movement the player didn't initiate causes sim sickness
- **Comfort modes**: always provide: teleport locomotion, snap turning, vignette during movement

### Interaction Design
- Dominant hand for primary actions; non-dominant for menu/secondary
- Direct manipulation feels natural: reach out and grab
- Haptics confirm every important interaction (short pulse on grab/release)
- Arm's length: UI elements 0.5-1.5m from player; never closer than 0.5m (eye strain)
- Scale: real-world proportions (a door should feel like a door)

### Platform Selection
| Platform | Best For |
|----------|----------|
| Meta Quest (standalone) | Widest audience, no PC required |
| PCVR (SteamVR) | Highest fidelity, smaller audience |
| ARKit (iOS) | Consumer AR on iPhone/iPad |
| ARCore (Android) | Consumer AR on Android |
| HoloLens 2 | Enterprise AR |

### Unity XR Toolkit
- `XROrigin`: root of XR rig (replaces deprecated `XRRig`)
- `XRController`: maps physical controller input to Unity actions
- `XRInteractionManager`: manages interactables and interactors
- `XRGrabInteractable`: makes any object grabbable with one component

---

---

## game-design

**When to use:** Designing game systems, writing a Game Design Document (GDD), balancing gameplay, or applying player psychology principles.

### The 30-Second Core Loop Test
Every game must have a fun 30-second loop:
```
ACTION → Player does something
FEEDBACK → Game responds immediately (sound, visual, number pop)
REWARD → Short-term goal achieved (kill, collect, progress)
REPEAT → Compelling reason to do it again
```

If the 30-second loop isn't fun in isolation, no amount of content/story will save the game.

### Game Design Document (GDD) Structure
1. **Concept** — One sentence: "What is this game?"
2. **Core Loop** — The 30-second / 5-minute / 30-minute loop diagram
3. **Player Fantasy** — What does the player feel like? (power fantasy, discovery, mastery)
4. **Mechanics** — Detailed rules for each system
5. **Progression** — How player/world state changes over time
6. **Content Plan** — Levels, enemies, items, story beats
7. **Art Direction** — Visual style reference board
8. **Audio Direction** — Mood, instrumentation, reference tracks
9. **Platform & Technical** — Target hardware, engine, constraints
10. **Monetization** (if applicable)

### Player Psychology
| Principle | Application |
|-----------|-------------|
| **Variable reward schedule** | Random loot drops feel more compelling than fixed rewards (Skinner box — use ethically) |
| **Loss aversion** | Players work harder to avoid losing something than to gain something equivalent |
| **Mastery curve** | Teach mechanics slowly, introduce them gently, then combine them brutally |
| **Agency** | Give players meaningful choices; railroading kills engagement |
| **Flow state** | Challenge just above current skill level. Too easy = boredom. Too hard = anxiety. |

### Balancing Framework
1. **Playtest first**: feel beats math. If it feels wrong, the numbers are wrong.
2. **Identify the dominant strategy**: if there's always one best option, you have a balancing problem
3. **Rock/paper/scissors**: every unit/ability should have a counter
4. **Tuning parameters**: separate data from code (ScriptableObjects, JSON, spreadsheets) so designers can tune without engineering
5. **Analytics**: death heatmaps, level completion rates, item usage — data reveals unfairness

### Progression Systems
- **Character progression**: stats, skills, unlocks — gives players a sense of growth
- **World progression**: new areas, story beats, escalating challenge
- **Meta-progression**: roguelikes use this — permanent unlocks across runs
- Pacing rule: introduce new mechanic → let player practice → combine with previous mechanic → challenge

---

## game-art

**When to use:** Defining art style, setting up asset pipelines, or directing visual direction for a game.

### Art Style Selection
Choose style based on: team capability + scope + target emotion + technical constraints

| Style | Good For | Tools |
|-------|----------|-------|
| Pixel art | Retro feel, solo/small team, mobile | Aseprite, Pixaki |
| Hand-drawn 2D | Charming, distinctive | Procreate, Clip Studio |
| Low-poly 3D | Performant, stylized, indie feel | Blender, Kenney assets |
| Realistic 3D | AAA expectation, high cost | Maya/Blender, Quixel |
| Vector/flat | Mobile, casual, scalable | Illustrator, Affinity |

### Asset Pipeline
```
Concept art → Rough sketch → Approved design
    ↓
Model/Illustration → UV unwrap (3D) / Export (2D)
    ↓
Texture → Compress (ASTC/ETC2 mobile, DXT PC)
    ↓
Import to engine → Atlas/bundle → Runtime
```

### Animation Workflow
- **Spritesheet**: frame-by-frame; Aseprite → export JSON + PNG atlas
- **Skeletal (2D)**: Spine, Dragonbones — deform and animate bones, not pixels; smoother, smaller file size
- **3D animation**: Blender rigging → FBX export → Mecanim (Unity) / AnimationTree (Godot)
- Animation states: idle, walk, run, jump, attack, hurt, death — minimum set for any character

### Style Guide Checklist
- [ ] Color palette defined and limited (16-32 colors for pixel art; brand palette for stylized 3D)
- [ ] Lighting style decided (flat, cel-shaded, realistic)
- [ ] Reference board created and shared with all artists
- [ ] Asset naming convention documented
- [ ] Folder structure enforced in version control

---

## game-audio

**When to use:** Designing sound effects, integrating music, implementing adaptive audio systems, or setting up FMOD/Wwise.

### Audio Category System
| Category | Behavior | Examples |
|----------|----------|---------|
| **Music** | Looping, crossfade, ducking | BGM, combat music, ambient |
| **SFX** | One-shot, positional (3D) | Footsteps, impacts, UI clicks |
| **Voice** | Triggered, subtitles sync | Dialogue, barks, narration |
| **Ambient** | Looping, layered, positional | Wind, crowd, machinery |

### Adaptive Audio Patterns
- **Vertical layering**: add/remove music layers based on game state (combat adds percussion layer, tension adds strings)
- **Horizontal re-sequencing**: transition between musical phrases at musically appropriate points (not abrupt cuts)
- **Parameter-driven**: tie music intensity to a float (0.0 = calm → 1.0 = high combat) and blend in real-time

### FMOD Integration (Unity)
```csharp
// Play 3D positioned sound
[FMODUnity.EventRef] public string footstepEvent;

void PlayFootstep(Vector3 position) {
    FMOD.Studio.EventInstance instance = FMODUnity.RuntimeManager.CreateInstance(footstepEvent);
    instance.set3DAttributes(FMODUnity.RuntimeUtils.To3DAttributes(position));
    instance.start();
    instance.release(); // auto-releases when done
}

// Set parameter for adaptive music
void SetCombatIntensity(float intensity) {
    musicInstance.setParameterByName("CombatIntensity", intensity);
}
```

### Sound Design Principles
- **Contrast**: silence makes sounds louder. Don't fill every moment.
- **Feedback hierarchy**: player-caused sounds > environmental > background music
- **Emotional reinforcement**: music and SFX should agree on the emotional tone
- **Mobile**: users often play without sound — UI feedback must work visually too

---

---

## multiplayer

**When to use:** Designing multiplayer architecture, implementing networking, handling synchronization, or debugging lag/desync issues.

### Architecture Selection
```
What type of multiplayer?
├── Competitive / Real-time (FPS, fighting) → Client-Server + Rollback Netcode
├── Co-op / casual real-time → Client-Server + Lag Compensation
├── Turn-based / async → Peer-to-Peer or simple server relay
└── MMO / persistent world → Dedicated server, authoritative
```

### Authoritative Server Pattern (Standard)
- **Client**: sends inputs, predicts own movement locally
- **Server**: authoritative — validates all actions, resolves conflicts
- **Client reconciliation**: if server disagrees with client prediction, snap back and replay inputs
- Never trust the client for: damage dealt, item pickup, position for game logic

### Rollback Netcode (Competitive Games)
1. Both clients simulate independently using inputs
2. When input arrives late: roll back to last confirmed frame, apply the late input, re-simulate
3. Players experience responsive input; network artifacts happen to opponent's character (less noticeable)
4. Used by: GGPO, most fighting games, some RTS

### Lag Compensation
- Server rewinds game state to when the client fired their shot
- Hit detection runs against the past state — player clicks a target that's now moved, but at their ping they saw them there
- Prevents "I shot him!" frustration; creates "I got shot around a corner!" — balance with max rewind time cap

### Common Synchronization Problems
| Problem | Cause | Fix |
|---------|-------|-----|
| Desync | Floating point differences | Use deterministic fixed-point math or server authority |
| Rubber banding | High latency + bad prediction | Improve client prediction, smooth reconciliation |
| Ghost hits | Lag compensation too generous | Cap max rewind time (150ms) |
| Cheating | Client-authoritative position | Move authority to server |

### Testing Multiplayer
- Test with artificial latency (100ms, 200ms, 500ms) from day one
- Test packet loss (1%, 5%, 20%)
- Simulate clock drift between clients
- Use two machines on same LAN before going over internet
