# Tokyo Odori Game Design

## Overview
A board game where players travel through Tokyo districts, collecting "Odori Tokens" by playing traditional folk songs. The goal is to reach the "Grand Finale" district with the highest score.

## Core Mechanics

### Scoring Formula
Each song has a base score calculated from:
- **Population** (0-1000): More populous areas = higher base
- **Tourism** (0-1000): Tourist popularity = higher base
- **Fame** (0-1000): Media exposure = higher base

**Score = (Pop × 0.4) + (Tour × 0.4) + (Fame × 0.2)**

### Game Board Layout
- **Start Zone**: Shibuya Crossing (Tokyo Odori Festival hub)
- **Districts** (clockwise):
  1. Shibuya (Tokyo Odori Festival) - High Fame
  2. Harajuku - Medium Fame
  3. Shinjuku - Medium Population
  4. Asakusa - Low Fame
  5. Roppongi - High Tourism
  6. Akihabara - Medium Population
  7. Ginza - High Fame
  8. Ikebukuro - Medium Population
  9. Kichijoji - Low Fame
  10. Nakano - Medium Population
  11. Yokohama - High Tourism
  12. Kawasaki - Low Fame
  13. Sendai (bonus round) - Special event
  14. Grand Finale (Tokyo Tower) - Win condition

### Player Tokens
- **Odori Token** (collected by landing on a district and playing its song)
- **Bonus Tokens** (extra points for visiting tourist-heavy districts)
- **Fame Points** (earned by collecting songs from high-fame districts)

### Game Flow
1. Roll dice (1-6) to move forward
2. On landing, choose a song from that district's track list
3. Calculate score using the formula
4. Collect Odori Token
5. If you reach Grand Finale, win!

## Song Selection
From the 14 tracks in `min-yoh-abc`:

| # | Track | Region | Score | Theme |
|---|-------|--------|-------|-------|
| 1 | 東京音頭 | 東京都 | 4000 | Grand Finale (final destination) |
| 2 | 佐渡おけさ | 新潟 | 2000 | Coastal festival |
| 3 | 津軽じょんから節 | 青森 | 1500 | Mountain folk |
| 4 | まつおさだ節 | 山形 | 1200 | Rural celebration |
| 5 | そばすき節 | 山形 | 1000 | Farm life song |
| 6 | どさんこ節 | 岩手 | 1200 | Agricultural tradition |
| 7 | ハマチ節 | 千葉 | 1500 | Coastal fishing village |
| 8 | 銭形おどり | 京都 | 2500 | Paper doll dance |
| 9 | 阿波おどり | 徳島 | 3000 | Southern island festivity |
| 10 | よさこい節 | 高知 | 2800 | Southern island rhythm |
| 11 | よしや節 | 熊本 | 1500 | Southern festival |
| 12 | きりこぶし | 富山 | 1000 | Northern mountain tune |
| 13 | おともやん | 愛媛 | 1200 | Island community song |
| 14 | ひえつき節 | 福島 | 1300 | Central Japan folk |

## Implementation Files

### `minyo_db/scores.json`
```json
{
  "tokyo_odori": {
    "region": "東京都",
    "pop_rank": 1,
    "tour_rank": 1,
    "fame_rank": 1,
    "score": 4000
  },
  ...
}
```

### `neko_minyo/generate.py`
```python
import random
from dataclasses import dataclass

@dataclass
class Song:
    name: str
    region: str
    pop_rank: int
    tour_rank: int
    fame_rank: int
    score: int

# Load scores from minyo_db
# Generate random song selection based on dice roll
# Calculate score using weighted formula
```

### `neko_minyo/zine_layout.py`
HTML template for the zine pages showing each track with score breakdown.

## Quick Start Guide
1. Place token on Shibuya (starting zone)
2. Roll die (1-6) to move
3. Pick a song from the current district's track list
4. Calculate score: (pop×0.4)+(tour×0.4)+(fame×0.2)
5. Move forward by score amount
6. Repeat until reaching Grand Finale

## Variant Ideas
- **Tourist Bonus**: Visiting tourist-heavy districts (+50 points)
- **Fame Boost**: Playing high-fame songs twice gives extra bonus
- **Time Limit**: 30-minute game with limited turns
- **Co-op Mode**: Players combine scores to reach the finale together

---
*Game designed for the min-yoh-abc project (neo-minyo repo)*
*Based on the 14-track playlist with ranked scores*