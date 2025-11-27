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

- **Enhanced Nightlords:** Harder versions of the standard Nightlords with increased health, damage, and altered attack patterns. These provide greater challenge and significantly increased difficulty.

- **Game Difficulties:** 
  - *Deep of Night: Depth (1-5):* Progressively harder difficulty tiers with ranking systems

- **Runes:** In-game currency earned by defeating enemies, used to level up the character (max level 15 per run).

- **Team Composition:** Players can tackle runs solo, in duos, or trios, either with friends or random matchmaking.
---

## Research Questions

1. **What factors influence how far I progress in a run?**
   - Which variables most strongly predict progression through the stages (first_day → second_day → final_day → victory)?
   - Can we build a model that forecasts expected run outcome?
   - What distinguishes early failures from near-victory runs?
2. **What is the optimal resource allocation strategy under time constraints?**
   - **Time is limited in each run** - players must choose between:
     - **Evergaols** (0-7): Provide combat buffs, consume moderate time
     - **Great Enemies**: Drop valuable loot, consume time
     - **Middle Castle**: Provides premium loot, but requires significant time investment
   - Is there an optimal balance between these activities?
   - **Does team size affect optimal strategy?**
     - Can trios split up to cover more content efficiently?
     - Do duos need to be more selective about risk-taking?
   - Does the optimal strategy change by difficulty level or character?
   - What's the point of diminishing returns for evergaol clearing?
3. **Which character (Nightfarer) do I perform best with?**
   - Does this vary by game difficulty or final boss (Nightlord)?
   - Do certain characters benefit more from specific resource allocation strategies?
4. **Does session progression affect performance (warm-up effect)?**
   - Do I perform significantly better in later runs?
   - Is there an optimal "warm-up" period before peak performance?
   - At what run index does performance plateau or decline due to fatigue?
5. **How do RNG and luck factors influence outcomes?**
   - Does map variation meaningfully affect success rates?
   - Can we quantify the impact of randomness versus player strategy?
---

## Dataset

### Overview
- **Source:** Personal gameplay data from Elden Ring Nightreign (FromSoftware, 2025)
- **Collection Period:** September 2025 - Present
- **Current Size:** 121 completed runs
- **Target Size:** 200+ runs by project completion
- **Variables:** 16 per run

### Variables

| Variable | Type | Description |
|----------|------|-------------|
| `run_id` | Numeric | Unique identifier for each run |
| `run_index_in_day` | Numeric | Position of run within gaming session |
| `character` | Categorical | Character played (recluse, revenant, wylder, guardian) |
| `difficulty` | Categorical | Difficulty mode (depth1/2/3/4/5) |
| `nightlord` | Categorical | Boss faced (Gladius, Caligo, Adel, Fulghor, Gnoster, Heolstor, Libra, Maris) |
|`enhanced` | Boolean | Whether the Nightlord is enhanced version |
| `map` | Categorical | Map variant (base, crater, rotted_woods, mountaintop, noklateo) |
| `run_outcome` | Ordinal/Categorical | Result (ordered by progression: first_day < second_day < final_day < victory) |
| `evergaol_cleared` | Numeric | Number of optional challenges completed (0-7) |
| `middle_castle_visited` | Boolean | Whether player visited middle castle |
| `great_enemies_cleared` | Numeric | Number of great-enemies defeated |
| `enemies_cleared` | Numeric | Number of normal enemies defeated |
| `team_type` | Categorical | Solo, duo, or trio |
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
- Success rate by character, difficulty, and difficulty
- Performance metrics across `run_index_in_day` (warm-up analysis)
- Correlation heatmaps between continuous variables
- Box plots comparing strategic decisions (castle visits, evergaols)
- Time series of performance over gaming sessions


----

## Limitations and Future Work

### Current Limitations
- **Single-player perspective:** No data from other players for comparison
- **Manual collection:** Potential for recording errors
- **Limited sample size:** Some categories have few observations particularly enhanced Nightlords and maps other than base.

### Future Directions
1. **Expand dataset:**
   - Collect data from friends for comparative analysis
   
2. **Practical applications:**
   - Real-time performance prediction tool
   - Personalized strategy recommendations
   - Extend to other roguelike games

3. **Automated Data Collection**
   - Data collection through in-game APIs such as Overwolf 
