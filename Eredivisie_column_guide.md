# Eredivisie Merged Dataset: Column Guide

File: `Eredivisie_2024-2027_merged.csv`
Seasons: 2024/25, 2025/26 and 2026/27 (up to 8 Nov 2026)
Size: 720 matches, 89 columns
Source of the column names: [football-data.co.uk](https://www.football-data.co.uk)

---

## 1. Match info

| Column | Meaning |
|---|---|
| `Season` | Season label (added during the merge) |
| `Date` | Match date, formatted `yyyy-mm-dd` |
| `Time` | Kick-off time |
| `HomeTeam` | Home team |
| `AwayTeam` | Away team |

## 2. Results

| Column | Meaning |
|---|---|
| `FTHG` | Full-time goals, home team |
| `FTAG` | Full-time goals, away team |
| `FTR` | Full-time result: `H` home win, `D` draw, `A` away win |
| `HTHG` | Half-time goals, home team |
| `HTAG` | Half-time goals, away team |
| `HTR` | Half-time result: `H`, `D` or `A` |
| `HxG` | Expected goals, home team (2026/27 only, empty for earlier seasons) |
| `AxG` | Expected goals, away team (2026/27 only, empty for earlier seasons) |

## 3. Match statistics

In each pair, the first column is the home team and the second is the away team.

| Home | Away | Meaning |
|---|---|---|
| `HS` | `AS` | Shots |
| `HST` | `AST` | Shots on target |
| `HF` | `AF` | Fouls committed |
| `HC` | `AC` | Corners |
| `HY` | `AY` | Yellow cards |
| `HR` | `AR` | Red cards |

---

## 4. Betting odds

All odds are **decimal odds** (e.g. `2.50` pays 2.50 per 1 staked, stake included).

### 4.1 Bookmaker prefixes

| Prefix | Source |
|---|---|
| `B365` | Bet365 |
| `BW` | Bet&Win |
| `BFE` | Betfair Exchange |
| `Max` | Highest odds offered by any bookmaker in the survey |
| `Avg` | Average odds across the bookmakers in the survey |

### 4.2 Reading a column name

A column name is built from these parts:

```
[Bookmaker] [C = closing] [market / outcome]
```

| Part | Meaning |
|---|---|
| No `C` after the bookmaker | Odds at collection time, usually a few days before kick-off |
| `C` after the bookmaker | **Closing odds**, taken just before kick-off (usually the most accurate) |

### 4.3 Markets

**Match result (1X2)**: last letter is the outcome.

| Suffix | Outcome |
|---|---|
| `H` | Home win |
| `D` | Draw |
| `A` | Away win |

Examples: `B365H` is Bet365's odds on a home win. `AvgCD` is the average closing odds on a draw.

**Total goals, over/under 2.5**

| Column pattern | Meaning |
|---|---|
| `...>2.5` | Odds on **over** 2.5 total goals |
| `...<2.5` | Odds on **under** 2.5 total goals |

Examples: `Max>2.5`, `B365C<2.5`.

**Asian handicap**

| Column | Meaning |
|---|---|
| `AHh` | Handicap line for the home team (e.g. `-0.5` means the home side starts half a goal behind) |
| `AHCh` | Same handicap line, at closing |
| `...AHH` | Odds on the **home** team at that handicap |
| `...AHA` | Odds on the **away** team at that handicap |

Examples: `MaxAHH` is the highest odds on the home side at the handicap. `AvgCAHA` is the average closing odds on the away side.

---

## 5. Quick examples

| Column | Plain-English meaning |
|---|---|
| `FTR` | Who won at full time |
| `HST` | Home shots on target |
| `B365H` | Bet365 odds on a home win |
| `MaxCA` | Best closing odds on an away win |
| `AvgC<2.5` | Average closing odds on under 2.5 goals |
| `BFECAHH` | Betfair Exchange closing odds on the home side at the closing handicap |

## 6. Notes

- Some odds columns have small gaps. Most are under 5% empty, but `BFEAHH` and `BFEAHA` are about 35% empty.
- `HxG` and `AxG` are only filled for 2026/27.
- For results and stats only, the columns up to `AR` are all you need.
