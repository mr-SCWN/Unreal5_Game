# Unreal5_Game

A small Unreal Engine 5 third-person combat prototype built mostly in **Blueprints**.  
The project focuses on a simple arena loop: enter an arena → enemies spawn → fight → doors open when the wave is cleared.

---

## Features

### Player
- Third-person character
- Melee attacks (damage via **ApplyDamage**)
- Stamina system (used for actions like sprint/attacks depending on setup)
- Health / death flow with Game Over UI

### Enemies (AI + Combat)
Enemies use a lightweight Blueprint AI logic (no Behavior Tree required):
- **Chase / return to home** behavior
- **Attack with cooldown**
- **Take damage / die**
- **Enemy HP bar** displayed above the enemy (Widget Component)

Enemy types implemented:
- **Goblin**
  - Basic melee attack
  - Jump attack (triggered randomly every few attacks, tuned in BP)
- **Mage**
  - Keeps distance from the player
  - Stops moving during casting
  - Shoots a projectile (spawned + damage on hit)
  - Teleport within allowed area / NavMesh bounds (arena-limited)
  - Switches to melee if the player is too close
- **Golem**
  - Basic melee attack
  - AOE slam attack (player can dodge by jumping)
  - AOE telegraph/debug messages can be enabled/extended

### Arena System
- Arena trigger that starts a wave when the player enters
- Spawns a configured number of enemies at TargetPoints
- Tracks alive enemies and opens doors when cleared
- Debug option: **Kill All Enemies** button/event (for testing)

### UI
- Main HUD: Player HP + Stamina (bar + numeric values)
- Enemy HP bar above each enemy
- Game Over screen
- Victory / arena cleared flow

### Misc
- Pixel-art UI icons (sword, heal)
- Project organized into logical folders (Blueprints / Enemies / UI / etc.)

---

## Controls (example)
> Adjust to your actual keybinds if different:
- Move: **WASD**
- Camera: **Mouse**
- Attack: **LMB**
- Jump: **Space**
- Sprint: **Shift**
- Heal: (if enabled) **E**
- Debug: Kill all enemies: **=**

---

## How to Run
1. Open the project in **Unreal Engine 5**.
2. Open the main map/level (arena level).
3. Press **Play**.
4. Enter the arena trigger to start the enemy wave.

---

## Notes / Known Areas to Improve
- Polishing hit reactions and ensuring death animations are fully uninterruptible in every edge case
- Extra enemy abilities / balancing
- Better AOE telegraphs (decals / particles instead of debug strings)
- More robust crowd avoidance / collision behavior for multiple enemies

---

## Tech
- **Unreal Engine 5**
- Mostly **Blueprints**
- Damage system: **ApplyDamage / AnyDamage**
- AI movement: **AI MoveTo**
- Animations: **AnimBP + Montages (slots)**

---

## License
This project is for learning / portfolio purposes.  
Assets (models/animations) may have their own licenses depending on source — check your imported asset packs.
