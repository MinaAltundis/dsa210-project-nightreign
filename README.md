# Analyzing Success Factors in Elden Ring Nightreign

## DSA 210 Fall 2025-2026 Term Project

**Student:** Mina Altundiş  

---

## Table of Contents
- [Motivation](#motivation)
- [Research Questions](#research-questions)
- [Dataset](#dataset)
- [Data Collection](#data-collection)
- [Planned Analysis](#planned-analysis)
- [Limitations and Future Work](#limitations-and-future-work)

---

## Motivation

Elden Ring Nightreign is a roguelike action RPG where players complete multiple runs per gaming session, with each run resetting upon completion. As an active player, I've observed that my performance varies significantly across different runs, characters, and strategic decisions. However, it's unclear which factors most strongly influence success.

This project aims to **identify and quantify the key factors that lead to successful runs** in Nightreign, providing data-driven insights for gameplay optimization. Understanding these patterns has practical value for improving my own performance and could reveal interesting behavioral patterns in roguelike gaming.

### Game Context

To understand the dataset, here are the key game mechanics:

- **Run Structure:** Each expedition lasts 3 in-game days. Players explore during the day, fight bosses at night, and face a final "Nightlord" boss on day 3. Success means defeating the Nightlord; failure can occur on any day.

- **Nightfarers (Characters):** Players choose from 8 unique characters, each with different abilities. Examples: Recluse (magic user), Revenant (summoner), Wylder (all-rounder), Guardian (tank).

- **Evergaols:** Optional mini-dungeons scattered across the map. Clearing them provides powerful rewards but consumes time and resources. Players must decide how many to attempt (0-7 per run).

- **Middle Castle:** A central landmark containing valuable loot and upgrades. Visiting requires deviating from the optimal path but offers significant rewards.

- **Nightlords:** Eight powerful bosses that serve as the final challenge. Each has unique mechanics and weaknesses that need to be accomodated for (e.g., Gladius, Caligo, Fulghor).

- **Loot Quality:** Weapons and items have rarity tiers (1-5, from common to legendary). Higher quality loot provides better stats and passive abilities, significantly impacting combat effectiveness.

- **Game Modes:** 
  - *Normal:* Standard difficulty
  - *Enhanced:* Increased challenge with better rewards
  - *Deep of Night (1-5):* Progressively harder difficulty tiers with ranking systems

- **Runes:** In-game currency earned by defeating enemies, used to level up the character (max level 15 per run).

- **Team Composition:** Players can tackle runs solo, in duos, or trios, either with friends or random matchmaking.
---

## Research Questions

1. **What factors most strongly predict run success?**
   - Which variables have the highest correlation with achieving victory versus defeat?
   - Can we build a predictive model to forecast run outcomes?
2. **How do strategic decisions impact run outcomes?**
   - Does visiting the middle castle increase success rates?
   - Does clearing more evergaols lead to better performance?
   - Do duo or trio teams have higher success rates?
3. **Which character (Nightfarer) I perform best with, and does this vary by game mode or final boss (Nightlord)?**
4. **Does session progression affect performance (warm-up effect)?**
   - Do I perform significantly better in later runs compared to my first run of each gaming session?
   - Is there an optimal "warm-up" period before peak performance?
   - At what run index does performance plateau or decline due to fatigue?
5. **How do RNG and luck factors influence outcomes?**
   - How does loot quality obtained correlate with final outcomes?
   - Does map variance affect success rates?
---

## Dataset

### Overview
- **Source:** Personal gameplay data from Elden Ring Nightreign (FromSoftware, 2025)
- **Collection Period:** September 2025 - Present
- **Current Size:** 96 completed runs
- **Target Size:** 200+ runs by project completion
- **Variables:** 16 per run

### Variables

| Variable | Type | Description |
|----------|------|-------------|
| `run_id` | Numeric | Unique identifier for each run |
| `run_index_in_day` | Numeric | Position of run within gaming session |
| `character` | Categorical | Character played (recluse, revenant, wylder, guardian) |
| `game_mode` | Categorical | Difficulty mode (normal, enhanced, deep_of_night1/2/3/4/5) |
| `nightlord` | Categorical | Boss faced (Gladius, Caligo, Adel, Fulghor, Gnoster, Heolstor, Libra, Maris) |
| `map` | Categorical | Map variant (base, crater, rotted_woods, mountaintop, noklateo) |
| `run_outcome` | Categorical | Result (victory, final_day, second_day, first_day) |
| `evergaol_cleared` | Numeric | Number of optional challenges completed (0-7) |
| `middle_castle_visited` | Boolean | Whether player visited middle castle |
| `great_enemies_cleared` | Numeric | Number of great-enemies defeated |
| `enemies_cleared` | Numeric | Number of normal enemies defeated |
| `team_type` | Categorical | Solo, duo, or trio |
| `loot_quality_score` | Numeric | Quality of items obtained (1-5) |
| `allies_rescued` | Numeric | Number of times teammates were revived |
| `runes_obtained` | Numeric | In-game currency earned |
| `level` | Numeric | Final character level reached (1-15) |


---

## Data Collection

### Collection Method
Data is collected **manually after each gaming session** using a structured spreadsheet template.

### Process
**Post-run:** Data is provided by the game through the log system.

---

## Planned Analysis


#### Objectives
- Understand distributions of all variables
- Identify patterns and anomalies
- Visualize relationships between key variables
- Generate hypotheses for statistical testing

#### Planned Visualizations
- Success rate by character, game mode, and difficulty
- Performance metrics across `run_index_in_day` (warm-up analysis)
- Correlation heatmaps between continuous variables
- Box plots comparing strategic decisions (castle visits, evergaols)
- Time series of performance over gaming sessions


----

## Limitations and Future Work

### Current Limitations
- **Single-player perspective:** No data from other players for comparison
- **Manual collection:** Potential for recording errors
- **Limited sample size:** Some categories have few observations

### Future Directions
1. **Expand dataset:**
   - Collect data from friends for comparative analysis
   
2. **Practical applications:**
   - Real-time performance prediction tool
   - Personalized strategy recommendations
   - Extend to other roguelike games

3. **Automated Data Collection**
   - Data collection through in-game APIs such as Overwolf 
