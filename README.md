# 🤖 Project: [TBD Sci-Fi Roguelite Platformer] ⚡

## Project Vision & Game Design Document (GDD)

This document outlines the core concept, mechanics, and initial scope for this 2D roguelite action-platformer. The game focuses on **precise, high-stakes combat and movement** under escalating pressure.

### I. High-Level Overview

| Element | Description |
| :--- | :--- |
| **Concept Summary** | A challenging 2D Roguelite Action-Platformer where the player controls a fragile **Service Drone/Droid** escaping a **Cybernetic Facility**. Success relies on **precise combat, dash mobility, and parries** to defeat the Sector Guardian Boss under rapidly escalating difficulty. |
| **Genre** | Roguelite, Action-Platformer, **Precision Combat**, Sci-Fi. |
| **Target Audience** | Players who seek a high skill-ceiling, timing-based challenge, and roguelites where mechanical mastery is key. |
| **Engine Choice** | Godot or Unity2D |

### II. Core Experience & Mechanics

| Feature | Details & Focus |
| :--- | :--- |
| **Goal of a Run (Win State)** | Defeat the **Sector Guardian Boss**. A successful win is the *only* condition for retaining **Scrap Modules** (meta-currency). |
| **Protagonist** | **The Service Drone/Droid:** An agile but fragile maintenance unit. |
| **Tone/Feel** | **Tense, Deliberate, and Skill-Focused.** Success depends on timing the **Parry** and using the **Dash** for calculated offense and defense. |
| **Room Pressure** | **System Purge Meter.** Tiered threats (enemies, speed buffs, hazards) start every **10 seconds** in a room. |
| **Permanent Progression (Meta)**| Persistent currency is **"Scrap Modules"** (Scrap for short). Only earned by defeating the Boss. Dying results in the **loss of all Scrap** collected during that run. |

#### **Player Controls (Cross-Platform Mapping: Position-Consistent)**

Controls are mapped by the physical position of the button to ensure consistency across controllers (e.g., Jump is always the bottom face button).

| Action | Mouse / Keyboard | Xbox Controller | PlayStation Controller | Steam Deck / Switch Pro | Priority/Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Movement** | WASD / Arrow Keys | Left Stick / D-Pad | Left Stick / D-Pad | Left Stick / D-Pad | Directional input |
| **Jump** | **Spacebar** | **A** (Bottom) | **X** (Bottom) | **B** (Bottom) | Highest priority for verticality. |
| **Dash / Dodge** | **R-Click / Shift / X** | **B** (Right) | **Circle** (Right) | **A** (Right) | High priority for mobility and repositioning. |
| **Parry / Defense** | **Q / R-Bumper** | **RB** (Right Bumper) | **R1** (Right Bumper) | **RB** (Right Bumper) | **Critical** timing-based defensive move. |
| **Attack** | **L-Click / Z** | **X** (Left) | **Square** (Left) | **Y** (Left) | Main combat action (short-range). |
| **Interact / Pick Up**| E / F | Y (Top) | Triangle (Top) | X (Top) | Contextual action. |

***

## 🛠️ Project Breakdown: Minimum Viable Product (MVP) Tasks

This is the complete, ordered list of tasks required to build the core loop and systems.

### Phase 1: Core Movement & Defense

| Task ID | Status | Task Title | Description (The Specific Problem) |
| :--- | :--- | :--- | :--- |
| **A1** | [ ] | **Project Initialization** | Create a new 2D project and set up **all input mappings** (M/KB and Controller, per table above). Create the main scene file. |
| **A2** | [ ] | **Rigid Body & Jump** | Implement the 2D character controller. Add horizontal movement and a jump that features **variable jump height**. |
| **A3** | [ ] | **The Dash Mechanic** | Implement the **Propulsion Burst** (Dash). Must provide a fixed, instantaneous burst of movement and grant **temporary invulnerability** (i-frames). Set a short cooldown. |
| **A4** | [ ] | **Placeholder Art** | Design and import simple geometric sprites (or just use colored squares) for the Drone, platform tiles, and wall collision boxes. |
| **A5** | [ ] | **The Parry Mechanic** | Implement the **Parry move (RB/R1)**. Create a short-duration **Parry State** (e.g., 0.25 seconds) that blocks all damage. Set a short cooldown (e.g., 1 second). |

### Phase 2: Core Combat & Room Logic

| Task ID | Status | Task Title | Description (The Specific Problem) |
| :--- | :--- | :--- | :--- |
| **B1** | [ ] | **Melee Attack ([TBD Weapon Name])** | Implement the Drone's short-range attack. On press, generate a temporary hitbox in front of the Drone and check for `Hostile` collision. |
| **B2** | [ ] | **Grunt Drone Logic** | Create the first enemy object (**Service Bot**). Give it simple patrol behavior and **visual wind-up/tell** before it attacks. |
| **B3** | [ ] | **Health & Damage** | Implement a basic `Health` component and `TakeDamage` function. Display health (3 HP for player, 1 HP for Grunt) via debug text or simple UI icons. Implement a "death" state for both. |
| **B4** | [ ] | **Room Purge Gate** | Create a script that tracks the number of hostile entities in the room. The exit door object is locked until the `hostile_units_remaining` count reaches zero. |
| **B5** | [ ] | **System Purge Timer** | Implement a room timer UI that begins counting up upon room entry. When the timer hits the first threshold (e.g., 10 seconds), begin spawning 1 new **Service Bot** every 10 seconds (Tier 1 Pressure Event). |
| **B6** | [ ] | **Basic Boss Logic (Sector Guardian)** | Create a simple, contained **Boss Room**. Design the boss object with high HP and a very simple, observable attack pattern. Defeating it triggers the **Win State**. |

### Phase 3: Core Roguelite Variety

| Task ID | Status | Task Title | Description (The Specific Problem) |
| :--- | :--- | :--- | :--- |
| **C1** | [ ] | **Core Upgrade System** | Implement a generic **Upgrade Chip** item that, when collected, grants one of the defined passive upgrades (e.g., +1 Health). |
| **C2** | [ ] | **Parry Feedback & Riposte** | Modify the enemy/Parry scripts: If a Parry collides with an enemy attack hitbox, immediately apply a **Stun status** (Riposte State) to the enemy for 1 second, making them vulnerable to follow-up damage. |
| **C3** | [ ] | **Ranged Enemy Implementation** | Create a second enemy type (**Sentry Bot**). Give it stationary or fixed-path patrol behavior and a **simple projectile attack** fired when the player is in range. |
| **C4** | [ ] | **Simple Weapon Modifier** | Create one **Attack Modifier** item (e.g., **Wide Arc**). When the player picks it up, their basic attack is replaced or modified (e.g., the attack hitbox is 50% wider). |

### Phase 4: UI and Flow

| Task ID | Status | Task Title | Description (The Specific Problem) |
| :--- | :--- | :--- | :--- |
| **D1** | [ ] | **Main Menu UI** | Implement the Main Menu scene with functional buttons: Start Run, Enter Hub, Quit. |
| **D2** | [ ] | **In-Game HUD** | Design and implement the basic In-Game HUD (Health, and the visual display for the **System Purge Meter/Timer**). |
| **D3** | [ ] | **Hub Screen UI** | Implement the Hub Scene UI: Display **Total Scrap Modules** (persistent global stat) and a placeholder button for the upgrade store. |
| **D4** | [ ] | **Win/Loss Flow** | Implement the final flow logic: If player dies, **wipe run-specific Scrap Modules**. If player defeats **Boss (B6)**, add run-specific **Scrap Modules** to global total, then show Win Screen. |
