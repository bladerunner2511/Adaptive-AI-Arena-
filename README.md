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
---
## How the Adaptive AI Works

At the end of every wave, the system evaluates your behaviour assesing things like:

- Melee and ranged attack counts and accuracy
- Kill breakdown by enemy type and attack type
- Wave completion time
- Average player movement speed

From this data it adjusts the enemies accordingly for the next wave:

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
## Running the Project

### From Source
1. Clone or download the repository
2. Open the folder downloaded
3. Launch AdaptiveAIArena.exe

---
## Developer

**Kenneth Davies** — P2702519
**Supervisor** — Jethro Shell
**Institution** — De Montfort University
**Year** — 2026

---

## Licence

This project was developed as a Final Year Project and is intended for academic assessment purposes.
