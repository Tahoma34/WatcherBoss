# WatcherBoss
---

# 🧠 WatcherBoss – Epic Multi-Phase Boss Battles for Minecraft \[1.16.x – 1.20.x]

**WatcherBoss** is a highly configurable Minecraft plugin that introduces a multi-phase, tactical boss battle experience. Instead of mindlessly attacking a boss, players must first destroy defensive monuments that protect the boss from damage. This creates a dynamic and immersive PvE event filled with visual effects, countdowns, and reward systems.

---

## 🚀 Features

* 🔄 **Multi-phase combat** with monuments and a final vulnerability phase
* ⏳ **Dynamic countdown system** with scheduled messages before boss spawn
* 🧱 **Configurable monuments** with health, visuals, and interactivity
* 🎆 **Visual & sound effects** including particles, BossBars, and animations
* 🐷 **Final monument twist** with temporary boss invulnerability and surprise mob attacks
* 🎁 **Custom reward system** for top damage dealers
* 🧩 **PlaceholderAPI support** for dynamic in-game data
* 🔧 **Fully configurable** via YAML files (boss stats, locations, effects, rewards, messages)

---

## 📂 File Structure

### `config.yml`

Contains main plugin settings, including:

* Boss stats (HP, name, damage multiplier)
* Boss spawn timing and location
* Monument positions and health
* BossBar customization
* Reward tiers and commands

### `messages.yml`

All player-facing messages:

* Boss spawn alerts
* Monument damage/break notifications
* Final phase messages
* Victory announcements
* Countdown messages

---

## 📘 How It Works

### 🕒 1. Spawn Countdown

When the plugin is activated or `/watcherboss start` is used, a countdown begins. Players are notified at key intervals (e.g., 2m, 1m, 20s) via chat and titles.

### 💀 2. Boss & Monument Spawn

After the countdown, the boss spawns at a predefined location. Around it, monuments (special blocks) appear — each with their own HP and visual effects (particles, holograms).

### 🧱 3. Monument Phase

The boss cannot be damaged until all monuments are destroyed. Players must:

* Focus fire on monuments
* Watch their health bars decrease
* Coordinate during attacks

### 🛡️ 4. Final Monument Phase

The last monument adds a twist:

* When triggered, it makes the boss invulnerable again
* A wave of aggressive mobs (e.g., pigs) spawns
* After destroying the final monument, the boss becomes vulnerable

### 🔥 5. Battle & Effects

Throughout the fight, players will see:

* Custom BossBars
* Damage effects (e.g., explosion rings, particles)
* Attack animations
* Mob reinforcements (optional)

### 🏆 6. Victory & Rewards

Once the boss is defeated:

* Players are ranked based on damage
* Top 3 receive custom rewards (configurable commands/items)
* A final message announces the victors

---

## 🧪 Compatibility

* ✅ **Minecraft versions:** 1.16.x – 1.20.x
* ✅ **Server software:** Tested on Paper and Spigot
* ✅ **Java version:** Java 17+

---

## 💻 Commands

| Command               | Description                      |
| --------------------- | -------------------------------- |
| `/watcherboss start`  | Starts the boss spawn countdown  |
| `/watcherboss stop`   | Cancels the boss event           |
| `/watcherboss reload` | Reloads the plugin configuration |

---

## ⚙️ Configuration Examples

### Boss Settings (`config.yml`)

```yaml
# %watcherboss_timeleft% - PlaceHolderAPI

Boss:
  Name: "&cDevil's Keeper"
  Hp: 200.0              # Base boss health
  DamageAmplifier: 8     # Damage amplifier (e.g., INCREASE_DAMAGE effect level)

BossSpawn:
  MaxDistance: 50.0      # Maximum distance within which the boss should remain
  Interval: "0h 30m"      # Interval between spawns (e.g., 3 minutes)
  SpawnLocation:
    World: "world"
    X: -98.4
    Y: 88.0
    Z: -1.7

Monument:
  BlockType: "OBSIDIAN"  # Block used for the monument
  Health: 20.0           # Health of the monument
  DestructionDamage: 5.0
  BlindnessDuration: 60

BossMonuments:
  0:
    World: "world"
    X: -118.5
    Y: 87.0
    Z: -29.5
  1:
    World: "world"
    X: -78.5
    Y: 87.0
    Z: -29.5
  2:
    World: "world"
    X: -78.5
    Y: 87.0
    Z: 26.5
  3:
    World: "world"
    X: -118.5
    Y: 87.0
    Z: 26.5

LastMonument:
  Health: 25.0
  BlockType: "CRYING_OBSIDIAN"
  ActivatedMessage: "&cThe last monument has been activated! The boss is now invulnerable!"
  DestroyedMessage: "&aThe last monument has been destroyed! The boss is now vulnerable!"

BossBar:
  Title: "&cDevil's Keeper"       # Boss title in BossBar (color codes & -> § supported)
  Color: "PURPLE"                 # Color (RED, BLUE, GREEN, PURPLE, etc.)
  Style: "SEGMENTED_10"           # Style (SOLID, SEGMENTED_6, SEGMENTED_10, etc.)
  UpdateIntervalTicks: 20         # How often to update BossBar in ticks (20 = 1 sec)

BossRewards:
  top1:
    reward-1:
      chance: 0.6 # 1.0 = 100%, 0.1 = 10%
      actions:
        - give %player% diamond 5
        - give %player% golden_apple 3
        - "[message] &aYou have received a prize!"
    reward-2:
      chance: 0.4
      actions:
        - give %player% dirt 4
        - give %player% diamond_sword 1
        - "[message] &aYou have received a prize!"
    reward-3:
      chance: 0.2
      actions:
        - give %player% diamond_helmet 1
        - give %player% diamond_sword 1
        - "[message] &aYou have received a prize!"
  top2:
    reward-1:
      chance: 0.6
      actions:
        - give %player% diamond 5
        - give %player% golden_apple 3
        - "[message] &aYou have received a prize!"
    reward-2:
      chance: 0.4
      actions:
        - give %player% dirt 4
        - give %player% diamond_sword 1
        - "[message] &aYou have received a prize!"
    reward-3:
      chance: 0.2
      actions:
        - give %player% diamond_helmet 1
        - give %player% diamond_sword 1
        - "[message] &aYou have received a prize!"
  top3:
    reward-1:
      chance: 0.6
      actions:
        - give %player% diamond 5
        - give %player% golden_apple 3
        - "[message] &aYou have received a prize!"
    reward-2:
      chance: 0.4
      actions:
        - give %player% dirt 4
        - give %player% diamond_sword 1
        - "[message] &aYou have received a prize!"
    reward-3:
      chance: 0.2
      actions:
        - give %player% diamond_helmet 1
        - give %player% diamond_sword 1
        - "[message] &aYou have received a prize!"

BossMessages:
  BeforeSpawn:
    - "&f ───────── &e✦ &f─────────"
    - ""
    - "&f A deadly strike is about to be unleashed..."
    - "&f The boss will awaken in &c%left%&f!"
    - "&f Be prepared — there's no turning back!"
    - ""
    - "&f ───────── &e✦ &f─────────"

repeatChatSpawnMessages:
  - "20s"
  - "1m"
  - "2m"

  # List of messages for top players
  # You can use placeholders %player% and %damage%
chatTopMessages:
  - "&f─────────── &e✦ &f───────────"
  - ""
  - "&cA legend has been forged! The boss has fallen before heroes."
  - "&cThe bravest warriors of this battle:"
  - ""
  - "&fArena Champion: &c%top1_player% &7— &c%top1_damage% damage!"
  - "&fMonster Storm: &c%top2_player% &7— &c%top2_damage% damage!"
  - "&fSword Keeper: &c%top3_player% &7— &c%top3_damage% damage!"
  - ""
  - "&f─────────── &e✦ &f───────────"

InvulnerabilityEffect:
  CheckIntervalTicks: 700       # How often to burn and poison players (in ticks)
  Radius: 50.0                   # Effective radius around the boss
  BurnSeconds: 8                 # Duration players are set on fire (seconds)
  PoisonDurationTicks: 240       # Duration of poison effect (in ticks)
  PoisonAmplifier: 2             # Level of poison (0 = level I, 1 = level II, etc.)

VulnerableWave:
  intervalTicks: 340            # How often the boss releases a wave (in ticks)
  radius: 20.0                  # Maximum wave radius
  damage: 7.0                   # Damage from the wave
  particle: "VILLAGER_ANGRY"    # Type of particles used for the wave effect

PigAttack:
  Radius: 40                     # Radius within which the boss searches for players to "throw" pigs at
  ThrowIntervalTicks: 250        # Interval (in ticks) between pig throws (1 tick ~ 0.05 sec)
  ExplosionPower: 1.0            # Explosion power
  KnockbackPower: 2.0            # Knockback strength on players
  Damage: 10.0                   # Damage dealt upon hit
  SlowDurationTicks: 140         # Duration of slow effect (in ticks)
  SlowAmplifier: 2               # Level of slowness effect (0 = level I, 1 = level II, etc.)

AdditionalMobs:
  mob-1:                          # Configuration for an additional mob (can have multiple such sections)
    type: "PILLAGER"               # Type of mob (e.g., SKELETON, ZOMBIE, etc.)
    hp: 50.0                        # Health points of the mob
    speed: 0.5                      # Movement speed
    damage: 13.0                    # Damage the mob deals
    count: 10                       # Number of instances to spawn
    spawnInterval: 15               # Interval (in seconds) between spawning each instance

  mob-2:
    type: "RAVAGER"
    hp: 90.0
    speed: 0.6
    damage: 10.0
    count: 8
    spawnInterval: 30
```

---

## 📦 Dependencies

* [PlaceholderAPI (optional)](https://www.spigotmc.org/resources/placeholderapi.6245/)

---

## 🛠️ Installation

1. Download the plugin `.jar` file.
2. Place it in your `/plugins` directory.
3. Start or reload the server.
4. Configure `config.yml` and `messages.yml` to your liking.

---

## 📸 Screenshots & Demo

https://youtu.be/xGIf_3_vh3I

---

## 📣 Feedback & Support

Found a bug? Have suggestions or feature requests?
Feel free to open an [issue](https://github.com/Tahoma34/WatcherBoss/issues).

---

## 📃 License

This project is open-source and distributed under the [MIT License](LICENSE).

---

