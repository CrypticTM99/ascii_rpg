# ASCII RPG (Browser-based)

An entirely client-side, single-file ASCII RPG built with plain HTML/CSS/JavaScript. Explore dungeons, complete quests, earn gold and items, upgrade your gear, allocate skill points, challenge bosses, and now with pets, crafting, achievements, and daily challenges! 
This will be created as a nice template for others to use for their own projects! 
I will update this continuining development for my own itch.io version (itch.io/cryptictm) 

## Quick Start

- Open `index.html` (or whatever you choose to rename this file, e.g., `ascii_rpg_game.html`) in any modern desktop browser.
- No server, installs, or build steps required.

## Core Gameplay

- Town actions: Work jobs, use the blacksmith, rest, open the Quest Board, manage your Skill Tree, adopt pets, craft items, track achievements, and complete daily challenges.
- Dungeons: Enter different dungeons to fight randomized enemies and collect drops.
- Combat: Use Attack, Cast Spell, Use Item, or Run. The combat panel shows the current enemy and your scrolling log.
- Progression: Gain XP and gold from battles and quests. Leveling up awards skill points.

## UI Overview

- Town Area card: Job actions, blacksmith, rest, quest/skill UI toggles, pet system, crafting, achievements, and daily challenges.
- Dungeons card: Choose a dungeon (Rat Caves, Old Catacombs, Ashen Rift).
- Combat card: Combat actions, enemy ASCII art, and an internal scrolling log (newest entries at the bottom).
- Travel card: Move between `Hearthglen` and `Ashfall` (Ashfall requires level increase to enter).
- Quest Board card: Accept/track quests; includes Abandon Active Quest button.
- Inventory card: Shows item counts, gold, HP, level/XP, and gear level.
- Marketplace card: Random shop that refreshes every 5 minutes.
- Skill Tree card: Pick a class and allocate points to Power, Focus, Vitality.
- Pet System card: Adopt, feed, and care for ASCII art pets that provide combat bonuses.
- Crafting Workshop card: Combine materials to create new items and equipment.
- Achievements card: Track your accomplishments and earn rewards.
- Daily Challenges card: Special daily quests with unique rewards and streaks.

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

### NEW: Pet System
- Adopt ASCII art pets: Wolf Pup, Mystic Cat, Guardian Owl, Dragon Hatchling
- Pets provide combat bonuses (attack, spell, defense, or all stats)
- Feed pets with Pet Treats to maintain happiness
- Unhappy pets will run away
- Pet bonuses are automatically applied to combat

### NEW: Crafting System
- Combine materials to create new items
- Recipes: Magic Sword, Healing Potion, Stealth Cloak, Arcane Staff
- Materials include new crafting-specific items
- Crafted items have unique properties and values

### NEW: Achievement System
- Track progress on various goals
- Achievements: First Blood, Rat Slayer, Quest Master, Dungeon Crawler, Boss Slayer, Craftsman, Pet Lover, Arena Champion
- Rewards include gold, XP, and special items
- Progress is automatically tracked

### NEW: Daily Challenges
- Special daily quests with unique rewards
- Types: Kill Spree, Quest Rush, Crafting Day, Pet Care
- Rewards include gold, XP, and special items
- Streak system for consecutive completions

### Arena System
- Ashfall Arena with duels and wave challenges
- Earn Arena Tokens and Champion's Laurels
- Build reputation to unlock special challenges

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
    - NEW: Pet system: `togglePetSystem()`, `adoptPet(name)`, `feedPet()`, `playWithPet()`
    - NEW: Crafting: `toggleCrafting()`, `craftItem(recipeName)`, `canCraftRecipe(recipe)`
    - NEW: Achievements: `toggleAchievements()`, `checkAchievement(id)`, `renderAchievements()`
    - NEW: Daily Challenges: `toggleDailyChallenges()`, `startDailyChallenge()`, `claimDailyReward()`

## Balancing & Tuning (Suggested)

- Adjust base/level-based drop chances in `calculateDrop`.
- Tweak XP thresholds for leveling and the number of skill points awarded per level.
- Refine shop pricing ranges and item availability.
- Consider adding enemy damage/HP scaling by dungeon and level.
- Balance pet bonuses and happiness decay rates.
- Adjust crafting material requirements and recipe difficulty.
- Fine-tune achievement requirements and rewards.
- Balance daily challenge targets and rewards.

## Roadmap Ideas

### Version 0.7.0 - Enhanced Combat & Progression
- [ ] Multi-step quest lines and quest rewards that grant skill points or unique items
- [ ] Equipment slots (weapon/armor/trinket) instead of a single gear level
- [ ] Status effects and buffs/debuffs
- [ ] Critical hits and dodge mechanics
- [ ] Special abilities for each class

### Version 0.8.0 - World Expansion
- [ ] Additional towns and regions
- [ ] New dungeon tiers and boss encounters
- [ ] Seasonal events and limited-time content
- [ ] NPC interactions and reputation systems
- [ ] Guild/clan system

### Version 0.9.0 - Advanced Systems
- [ ] Prestige system with permanent bonuses
- [ ] Advanced pet evolution and breeding
- [ ] Player housing and decoration
- [ ] Trading system between players (localStorage-based)
- [ ] Mini-games and side activities

### Version 1.0.0 - Polish & Completion
- [ ] Sound effects and music (text-based descriptions)
- [ ] Advanced save/load with cloud sync options
- [ ] Modding support and plugin system
- [ ] Mobile optimization and touch controls
- [ ] Multiplayer features (local co-op)

## Current Version: 0.6.0

### What's New in 0.6.0
- **Pet System**: Adopt ASCII art pets that provide combat bonuses
- **Crafting System**: Combine materials to create new items and equipment
- **Achievement System**: Track progress and earn rewards for various goals
- **Daily Challenges**: Special daily quests with unique rewards and streaks
- **Enhanced Combat**: Pet bonuses automatically applied to attack, spell, and defense
- **New Items**: Pet treats, crafting materials, and prestige rewards
- **Improved Save System**: All new features are fully save/load compatible

### Technical Improvements
- Modular system architecture for easy expansion
- Comprehensive achievement progress tracking
- Daily challenge system with automatic refresh
- Pet happiness system with automatic decay
- Enhanced combat calculations with pet bonuses

## Credits

- Game created by cryptictm (2025) with contributions via pair-programming improvements.
- ASCII art adapted and crafted for an old-school terminal vibe.

## License
- GPL v3 International 
- Personal/educational use permitted. For commercial use or redistribution, please contact the author. 
