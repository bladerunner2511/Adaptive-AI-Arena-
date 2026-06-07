# Adaptive AI Arena

> A 2D side-on arena combat game where enemies adapt to how you play.

---

## Overview

Adaptive AI Arena is a wave-based arena combat game developed in Unity 6.4 as a Final Year Project. The core mechanic is an enemy AI system that analyses player behaviour between waves and dynamically adjusts enemy composition, stats and abilities to counter the player's dominant strategy.

No two runs feel identical. The longer you survive, the smarter the enemies get.

---

## Features

### Adaptive AI System
- Tracks melee vs ranged attack ratio, accuracy, movement speed and wave completion time
- Adjusts enemy spawn composition to counter the player's playstyle
- Scales enemy health and movement speed based on observed behaviour
- Assigns shields to enemy types killed predominantly by one attack type
- Streak bonus system — consecutive fast wave clears spawn reinforced orange enemies

### Combat
- Melee attacks with directional hitbox
- Ranged attacks with ammo and automatic regeneration
- Directional shield that blocks projectiles — limited duration with cooldown
- Hit flash and knockback feedback on all characters

### Enemy AI
- Two enemy types — melee (sword) and ranged (pistol)
- Finite state machines with Idle, Chasing, Attacking, Stunned states
- Platform jumping via diagonal raycasts
- Separation force to prevent stacking

### Arena
- 4 handcrafted maps with unique layouts
- Random map selection each wave — never repeats consecutively
- Map-specific enemy spawn points and health pickup locations
- Health pickup spawns at the start of every wave

### Progression
- Wave-based difficulty scaling — more enemies per wave
- Persistent leaderboard with top 10 entries
- Score system — kills, wave completion, damage penalty
- Score popup feedback on every point change

### UI & Polish
- Full HUD — health, ammo, shield bars and wave/score display
- Adaptation feed — animated notifications when enemies adapt
- Wave countdown before each wave
- Animated intro screen on game start
- Main menu with options, keybind remapping and leaderboard
- Game over screen with name entry and leaderboard submission

---

## Controls

| Action | Default |
|---|---|
| Move Left | A |
| Move Right | D |
| Jump | Space |
| Sprint | Left Shift |
| Drop Through Platform | S |
| Melee Attack | Left Click |
| Ranged Attack | Right Click |
| Shield | E |

All keybinds are remappable from the Options menu.

---

## How the Adaptive AI Works

At the end of every wave, the `AIDirector` evaluates a `WaveBehaviourSnapshot` containing:

- Melee and ranged attack counts and accuracy
- Kill breakdown by enemy type and attack type
- Wave completion time
- Average player movement speed

From this data it produces an `AdaptationProfile` applied to the next wave:

| Behaviour Observed | AI Response |
|---|---|
| Heavy melee usage | More ranged enemies spawn |
| Heavy ranged usage | More melee enemies spawn |
| Fast player movement | All enemies move faster |
| Quick wave completion | More enemies next wave |
| High accuracy | Enemies gain extra health |
| Enemies killed by ranged | That enemy type gains a shield |
| 5 consecutive fast waves | Bonus HP-boosted enemies appear |
| 10 consecutive fast waves | Bonus HP + speed boosted enemies appear |

---

## Technical Details

| Detail | Value |
|---|---|
| Engine | Unity 6.4 (LTS) |
| Language | C# |
| IDE | Visual Studio |
| Version Control | GitHub |
| UI | Unity UI Toolkit / TextMeshPro |
| Input | Unity Input System |
| Testing | Unity Test Framework (NUnit) |
| Platform | PC (Windows) |

---

## Project Structure

```
Assets/
├── Animations/         # Animator controllers and animation clips
│   ├── MeleeEnemy/
│   ├── Player/
│   └── RangedEnemy/
├── Audio/
│   ├── Music/
│   └── SFX/
├── Prefabs/            # Enemy, bullet, platform, pickup prefabs
├── Scenes/
│   ├── MainMenu
│   └── ArenaScene
├── Scripts/
│   ├── AI/             # AIDirector, PlayerBehaviourTracker, WaveBehaviourSnapshot, AdaptationProfile
│   ├── Arena/          # ArenaGenerator, CameraFollow, MapSpawnPoints, MapPickupPoint
│   ├── Audio/          # AudioManager
│   ├── Enemy/          # EnemyChase, RangedEnemy, EnemyHealth, EnemyAnimator, EnemyBullet, EnemyShieldVisual
│   ├── Pickups/        # HealthPickup, PickupManager
│   ├── Player/         # PlayerMovement, PlayerAim, PlayerHealth, PlayerMelee, PlayerRanged, PlayerShield, PlayerAnimator, AmmoSystem, Bullet, ShieldBlocker
│   ├── UI/             # HUDManager, MenuManager, GameOverUI, LeaderboardUI, AdaptationNotifier, AdaptationPanelUI, KeybindEntryUI, KeybindsPanelUI, ScorePopup, TransitionManager, WaveCountdown
│   └── Wave/           # WaveManager
├── Sprites/
│   ├── Background/
│   ├── Fighter/
│   ├── MeleeEnemy/
│   ├── Pistol/
│   ├── RangedEnemy/
│   ├── Sword/
│   └── Tiles/
└── Tests/
    ├── EditMode/       # AdaptiveAITests, ScoreTests, LeaderboardTests, SnapshotAIRulesTests, PlayerBehaviourTrackerTests, WaveScalingTests
    └── PlayMode/       # PlayerMovementTests, PlayerHealthTests, AmmoSystemTests
```

---

## Running the Project

### From Source
1. Clone the repository
2. Open the project in **Unity 6.4 (LTS)**
3. Open `Assets/Scenes/MainMenu`
4. Press **Play** in the Unity Editor

### Build
1. Go to **File → Build Settings**
2. Ensure `MainMenu` is scene index 0 and `ArenaScene` is scene index 1
3. Select **Windows x64**
4. Click **Build**

---

## Testing

The project includes 30+ unit tests using the Unity Test Framework.

To run them:
1. Open **Window → General → Test Runner**
2. Click **EditMode** → **Run All** for logic tests
3. Click **PlayMode** → **Run All** for runtime tests

---

## Developer

**Kenneth Davies** — P2702519
**Supervisor** — Jethro Shell
**Institution** — De Montfort University
**Year** — 2026

---

## Licence

This project was developed as a Final Year Project and is intended for academic assessment purposes.
