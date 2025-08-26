# ASCII RPG (Browser-based)

An entirely client-side, single-file ASCII RPG built with plain HTML/CSS/JavaScript. Explore dungeons, complete quests, earn gold and items, upgrade your gear, allocate skill points, and challenge bosses as you level your character to the fullest! 
This will be created as a nice template for others to use for their own projects! 
I will update this continuining development for my own itch.io version (itch.io/cryptictm) 

## Quick Start

- Open `index.html` (or whatever you choose to rename this file, e.g., `ascii_rpg_game.html`) in any modern desktop browser.
- No server, installs, or build steps required.

## Core Gameplay

- Town actions: Work jobs, use the blacksmith, rest, open the Quest Board, and manage your Skill Tree.
- Dungeons: Enter different dungeons to fight randomized enemies and collect drops.
- Combat: Use Attack, Cast Spell, Use Item, or Run. The combat panel shows the current enemy and your scrolling log.
- Progression: Gain XP and gold from battles and quests. Leveling up awards skill points.

## UI Overview

- Town Area card: Job actions, blacksmith, rest, quest/skill UI toggles.
- Dungeons card: Choose a dungeon (Rat Caves, Old Catacombs, Ashen Rift).
- Combat card: Combat actions, enemy ASCII art, and an internal scrolling log (newest entries at the bottom).
- Travel card: Move between `Hearthglen` and `Ashfall` (Ashfall requires level increase to enter).
- Quest Board card: Accept/track quests; includes Abandon Active Quest button.
- Inventory card: Shows item counts, gold, HP, level/XP, and gear level.
- Marketplace card: Random shop that refreshes every 5 minutes.
- Skill Tree card: Pick a class and allocate points to Power, Focus, Vitality.

## Systems

### Player
- HP/Max HP, Gold, Town, Gear Level, Level, XP
- Inventory tracked by item name and quantity

### Gear Upgrades
- Use the Blacksmith (costs gold + required material) to increase gear level for stronger attacks.

### Resting
- Fully restores HP at the inn.
- Restricted to out-of-combat only.

### Quests
- Quest Board refreshes periodically with a random selection of quests.
- Types: kill, killNamed, collect, travel.
- Progress updates automatically on kills, collection, or travel.
- You can abandon the active quest at any time using the Abandon button.

### Skills & Classes
- Skill Tree includes class selection (None, Warrior, Mage, Rogue) and three stats:
  - Power: +1 attack damage per point
  - Focus: +1 spell damage per point
  - Vitality: +5 max HP per point
- Leveling up awards skill points to allocate in the Skill Tree.

### Dungeons & Enemies
- Rat Caves, Old Catacombs, Ashen Rift (increasing difficulty and drop chances).
- Hearthglen high-level expansion: When in `Hearthglen` and level ≥ 10, additional enemy types can appear.
- Enemies display ASCII art on encounter.

### Items & Drops
- Item rarities: common, uncommon, rare, epic.
- Normal drop selection excludes boss weapons.
- Six new items added for Hearthglen level 10+ enemies: Boar Tusk, Bandit Emblem, Warden Leaf, Spider Silk, Cave Moss, Runed Shard.
- Boss-only weapons exist but are excluded from normal enemies.

### Boss: Vorthalon, Starbinder of Endlight
- Challengeable in Ashfall when level ≥ 15.
- Drops:
  - Guaranteed uncommon item(s)
  - Chance for one boss weapon (the only source of boss weapons)

### Shop/Marketplace
- Shows random non-boss items with prices ~80–120% of base value.
- Buy items (if you have enough gold) or sell items (for 60% of item base value).
- Refreshes automatically every 5 minutes.

## Controls

- Mouse-only. Click buttons in the cards to perform actions.
- Log shows action outcomes; newest entries appear at the bottom and the log auto-scrolls.

## Developer Notes

- Single HTML file app. No dependencies.
- Main elements of interest:
  - Layout/CSS in the `<style>` block
  - All game logic in the `<script>` block
  - Key functions:
    - `enterDungeon(name)`, `combat(action)`, `travel(destination)`
    - `log(message)` (appends and auto-scrolls)
    - Quest system: `initQuestPool()`, `refreshQuestsNow()`, `renderQuestList()`, `acceptQuest()`, `abandonQuest()`, `completeActiveQuest()`
    - Drop tables: `calculateDrop(dungeonName, playerLevel)`, `calculateVorthalonDrops(playerLevel)`
    - Skills: `toggleSkillTree()`, `setPlayerClass(value)`, `allocatePoint(stat)`, `awardSkillPointOnLevel()`, `updateSkillTreeUI()`

## Balancing & Tuning (Suggested)

- Adjust base/level-based drop chances in `calculateDrop`.
- Tweak XP thresholds for leveling and the number of skill points awarded per level.
- Refine shop pricing ranges and item availability.
- Consider adding enemy damage/HP scaling by dungeon and level.

## Roadmap Ideas

- More skill nodes and class-specific perks
- Equipment slots (weapon/armor/trinket) instead of a single gear level
- Multi-step quest lines and quest rewards that grant skill points or unique items
- Additional bosses and dungeon tiers
- Save/load using localStorage

## Credits

- Game created by cryptictm (2025) with contributions via pair-programming improvements.
- ASCII art adapted and crafted for an old-school terminal vibe.

## License
- GPL v3 International 
- Personal/educational use permitted. For commercial use or redistribution, please contact the author. 
