# ⚡ UltraEnchantments

> A production-ready Paper plugin that transforms Minecraft's enchantment system — extending vanilla enchants up to **level 100**, adding **21 custom enchantments**, a **Bow Mastery system** with universal cross-item enchants, endgame **Mythic Crystals**, and full admin tooling.

[![Paper](https://img.shields.io/badge/Paper-1.21.4-blue?logo=data:image/png;base64,...)](https://papermc.io)
[![Java](https://img.shields.io/badge/Java-21-orange?logo=openjdk)](https://adoptium.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Build](https://img.shields.io/badge/Build-Maven-red)](pom.xml)

---

## ✨ Features at a Glance

| Category | What's included |
|---|---|
| **Vanilla Extension** | All vanilla enchants up to level 100, tiered by player XP level |
| **Custom Enchants** | 14 general + 7 bow-exclusive enchantments, all configurable |
| **Bow Mastery** | 20 normally-restricted enchants (Sharpness, Fortune, Silk Touch…) unlocked on bows at 50+ XP |
| **Mythic Crystals** | Endgame item that upgrades any enchantment beyond normal table limits |
| **Storage** | SQLite (default) or MySQL with HikariCP connection pooling |
| **Economy** | Vault integration — enchanting costs optional in-game currency |
| **Placeholders** | Full PlaceholderAPI support |
| **Region Protection** | WorldGuard, GriefPrevention, and Lands respected for all AOE abilities |
| **Admin GUI** | In-game menus: Enchantment Guide, Leaderboard, Progression tracker |
| **Performance** | Anti-lag caps on all AOE operations, async DB writes, configurable thread pool |

---

## 📋 Requirements

| Requirement | Version |
|---|---|
| **Paper** (or Folia) | 1.21.4+ |
| **Java** | 21+ |

**Soft dependencies** (all optional, auto-detected):

- [Vault](https://github.com/MilkBowl/Vault) — economy costs for enchanting
- [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI) — `%ultraenchantments_*%` placeholders
- [WorldGuard](https://enginehub.org/worldguard/) — region protection
- [GriefPrevention](https://github.com/TechFortress/GriefPrevention) — claim protection
- [Lands](https://www.spigotmc.org/resources/lands.53313/) — land protection

---

## 🚀 Installation

1. Download the latest `.jar` from [Releases](../../releases).
2. Drop it into your server's `plugins/` folder.
3. Restart the server.
4. Edit `plugins/UltraEnchantments/config.yml` to your liking.
5. Reload with `/ultraenchant reload` (no server restart needed).

### Building from source

```bash
git clone https://github.com/yourname/ultraenchantments.git
cd ultraenchantments/plugins/mythic-enchantments
mvn clean package -DskipTests
# Output: target/UltraEnchantments-1.0.0.jar
```

---

## 🔮 Custom Enchantments

### General Enchantments (applicable to tools, weapons, armor)

| Enchantment | Applicable To | Effect | Max Level |
|---|---|---|---|
| **Super Miner** | Pickaxe | Mines a 3×3 grid of blocks instantly | 100 |
| **Super Lumberjack** | Axe | Fells entire trees in one swing | 100 |
| **Super Excavator** | Shovel | Shovels a 3×3 area instantly | 100 |
| **Mega Harvest** | Hoe | Harvests crops in a radius and auto-replants | 100 |
| **Vein Miner** | Pickaxe | Mines all connected ore of the same type | 100 |
| **Auto Smelt** | Pickaxe / Axe | Automatically smelts mined blocks | 100 |
| **Telekinesis** | Tools / Weapons | All drops go directly into your inventory | 100 |
| **Explosive Arrows** | Bow / Crossbow | Arrows explode on impact | 100 |
| **Multi Shot+** | Bow / Crossbow | Fires multiple arrows per shot | 100 |
| **Lightning Strike** | Sword / Axe | Chance to summon lightning on hit | 100 |
| **Frost Walker+** | Boots | Extended ice path; scales with level | 100 |
| **Life Steal** | Sword / Axe | Heals you for a portion of damage dealt | 100 |
| **Berserker** | Sword / Axe | Deal more damage the lower your HP | 100 |
| **Speed Miner** | Pickaxe | Grants Haste while mining | 100 |

### Bow Mastery Enchantments (bow/crossbow exclusive)

| Enchantment | Effect | Max Level |
|---|---|---|
| **Shadow Shot** | Arrows pierce through up to 8 enemies with 85–95% damage retention | 100 |
| **Sniper** | Damage scales with travel distance (+0.04/block/level, minimum 5 blocks) | 100 |
| **Hunter's Mark** | Struck targets glow (visible through walls) for up to 5+ minutes | 100 |
| **Gravity Shot** | Impact pulls all nearby mobs toward the hit point | 100 |
| **Freeze Shot** | Freezes targets with Slowness + Mining Fatigue + Powder Snow | 100 |
| **Chain Lightning** | Damage chains to up to 6 nearby mobs with visual lightning effect | 100 |
| **Piercing Infinity** | Infinite arrows always; Piercing I–V at levels 11–50; unlimited pierce at 51+ | 100 |

---

## 🏹 Bow Mastery — Universal Enchantments

Players with **50+ XP levels** have a chance to receive normally-restricted enchantments on bows via the enchantment table. Each has a minimum unlock level:

| Enchantment | Min. Player Level | Special Effect on Bows |
|---|---|---|
| Sharpness | 50 | Flat +0.5 damage/level per arrow |
| Smite | 50 | +2.5 damage/level vs undead |
| Bane of Arthropods | 50 | +2.5 damage/level vs arthropods + Slowness |
| Fire Aspect | 55 | Ignites targets for 4s/level |
| Knockback | 55 | Velocity push on arrow impact |
| Looting | 60 | Inherits vanilla looting drop bonus |
| Sweeping Edge | 60 | — |
| Efficiency | 65 | Grants Haste while holding the bow |
| Fortune | 65 | Multiplies mob drops by up to 30%/level |
| Silk Touch | 70 | 0.5%/level chance to drop a spawn egg |
| Frost Walker | 70 | — |
| Soul Speed | 75 | — |
| Depth Strider | 75 | — |
| Thorns | 80 | Reflects 5%/level of incoming damage |
| Protection | 80 | Passive Resistance while holding the bow |
| Blast Protection | 85 | — |
| Fire Protection | 85 | — |
| Projectile Protection | 85 | — |
| Density *(1.21+)* | 90 | +0.5 bonus damage/block of arrow fall distance |
| Breach *(1.21+)* | 90 | Up to 50% armor penetration |

---

## ⚙️ XP Level Requirements

Enchantments above level 5 require the **player** to have a minimum XP level:

| Enchant Level Range | Required Player Level |
|---|---|
| 1 – 5 | 0 (vanilla, free) |
| 6 – 10 | 40 |
| 11 – 20 | 50 |
| 21 – 30 | 60 |
| 31 – 40 | 70 |
| 41 – 50 | 80 |
| 51 – 60 | 90 |
| 61 – 70 | 100 |
| 71 – 80 | 110 |
| 81 – 90 | 120 |
| 91 – 100 | 130 |

All thresholds are fully configurable in `config.yml`.

---

## 💎 Mythic Crystals

**Mythic Crystals** are endgame items that upgrade enchantments beyond what the table normally allows.

- Hold an enchanted item and right-click with a Mythic Crystal to upgrade one enchantment
- Crystals have configurable drop rates from boss mobs, rare loot, or `/ultraenchant give`
- Upgrades are tracked in the database and shown on the leaderboard

---

## 🗄️ Database

| Mode | Config | Notes |
|---|---|---|
| **SQLite** (default) | `database.type: SQLITE` | Zero setup, stored in plugin folder |
| **MySQL** | `database.type: MYSQL` | Full HikariCP pool configuration available |

---

## 💬 Commands

| Command | Description | Permission |
|---|---|---|
| `/ultraenchant reload` | Reload config (no restart needed) | `ultraenchantments.command.reload` |
| `/ultraenchant give <player> <enchant> <level>` | Give an enchanted item | `ultraenchantments.command.give` |
| `/ultraenchant info <enchant>` | View enchantment details | `ultraenchantments.command.info` |
| `/ultraenchant guide` | Open the in-game enchantment guide GUI | `ultraenchantments.command.guide` |
| `/ultraenchant top` | Open the leaderboard GUI | `ultraenchantments.command.top` |
| `/ultraenchant debug` | Show debug info | `ultraenchantments.command.debug` |

**Aliases:** `/ue`, `ultraenchant`, `uenchant`

---

## 🔑 Permissions

```yaml
ultraenchantments.admin          # All admin permissions (op by default)
ultraenchantments.command.reload # Reload config
ultraenchantments.command.give   # Give enchanted items
ultraenchantments.command.debug  # Debug info
ultraenchantments.bypass.level   # Bypass XP level requirements
ultraenchantments.bypass.region  # Bypass region protection
ultraenchantments.bow-mastery    # Access all bow mastery features (all players by default)
```

Individual enchantment use permissions follow the pattern `ultraenchantments.enchant.<name>` (e.g. `ultraenchantments.enchant.shadow-shot`). All are `default: true` unless changed.

---

## 📄 Configuration Overview

`config.yml` is fully documented inline. Key sections:

```yaml
general:
  prefix: "&8[&6UltraEnchantments&8] &r"
  announce-level-100: true   # Global broadcast when anyone hits level 100

xp-requirements:
  100: 130   # Level 91-100 enchants need 130 XP levels

economy:
  enabled: true
  cost-per-level: 100.0
  scale-with-level: true

database:
  type: SQLITE   # or MYSQL

bow-mastery:
  universal-unlock-level: 50
  shadow-shot:
    max-level: 100
  # ... one section per bow enchantment
```

---

## 📊 PlaceholderAPI

| Placeholder | Returns |
|---|---|
| `%ultraenchantments_level_<enchant>%` | Current level of enchantment on held item |
| `%ultraenchantments_top_<enchant>%` | Server-wide top level for that enchantment |
| `%ultraenchantments_crystals%` | Number of Mythic Crystals the player has used |

---

## 🛡️ Performance & Anti-Lag

- All heavy operations (vein mining, tree felling, excavation) are processed **asynchronously** on a dedicated thread pool
- **Block-per-tick cap** (default 50) prevents lag spikes on massive operations
- **Entity count caps** on all AOE abilities (Gravity Shot: 20 entities, Shadow Shot: 8 targets, Chain Lightning: 6 jumps)
- **Arrow metadata** auto-purged after 30 seconds
- **DB writes** are batched (configurable interval, default every 5 seconds)
- All region-protection checks are synchronous and cached

---

## 🤝 Contributing

Pull requests are welcome! Please:

1. Fork the repo and create a feature branch
2. Follow the existing code style (no wildcard imports in new files, Javadoc on public methods)
3. Test on a Paper 1.21.4 server before submitting
4. Open a PR with a clear description of what changed and why

For bug reports, open an [Issue](../../issues) with your Paper version, plugin version, and a paste of the relevant stack trace.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙏 Credits

Built with:
- [Paper API](https://papermc.io) — Fast, async-friendly Minecraft server API
- [HikariCP](https://github.com/brettwooldridge/HikariCP) — High-performance JDBC connection pool
- [Vault](https://github.com/MilkBowl/Vault) — Economy abstraction layer
- [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI) — Placeholder framework
