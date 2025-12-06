---
layout: default
title: Settings Reference
permalink: /slp/settings-reference/
---

# Settings Reference

SexLab P+ uses two configuration files that serve different purposes:

| File | Location | Purpose |
|------|----------|---------|
| `SexLab.ini` | `SKSE\Plugins\SexLab.ini` | Core framework configuration (enjoyment rates, detection thresholds, etc.) |
| `Settings.yaml` | `SKSE\Plugins\SexLabData\Settings.yaml` | Your MCM preferences (auto-saved, persists across saves) |

This page documents the **SexLab.ini** settings that control the framework's internal behavior.

---

## Animation Settings

Settings controlling animation behavior and furniture handling.

| Setting | Default | Description |
|---------|---------|-------------|
| `fFurniturePreference` | 0.75 | Probability (0.0-1.0) that furniture will be used when starting a scene. |
| `fFurnitureScanRadius` | 750.0 | Radius (game units) to scan for usable furniture around actors. |
| `fMinScale` | 0.88 | Minimum actor scale for animation compatibility. |
| `bAllowDead` | false | Whether dead actors can participate in animations. |
| `fMinSetupTime` | 0.7 | Minimum time (seconds) for the "Starting" phase before transitioning to "Playing". |
| `fAdjustStepSizeIncrement` | 0.1 | Step increment for manual position adjustments. |
| `bAdjustNodes` | true | Enable automatic schlong/genital node adjustment during animations. |
| `fGhostModeAlpha` | 0.6 | Transparency alpha (0.0-1.0) for actors when ghost mode is enabled. |

### Furniture Detection

| Setting | Default | Description |
|---------|---------|-------------|
| `fFurnitureSquare` | 32.0 | Half-width of the square area scanned around furniture center. |
| `fFurnitureSquareHeight` | 128.0 | Height of the volume scanned above furniture for obstruction checking. |
| `fFurnitureSquareFloorSkip` | 16.0 | Height above floor to start scanning (avoids floor detection). |
| `fFurnitureSquareStepSize` | 8.0 | Step size when iterating through the furniture scan volume. |
| `fFurnitureTiltTolerance` | 10.0 | Maximum allowed tilt angle (degrees) for furniture to be usable. |

---

## Animation Filter Settings

Settings controlling animation selection scoring. Animations are scored based on how well actors match requirements.

| Setting | Default | Description |
|---------|---------|-------------|
| `iScoreAcceptThreshold` | 1 | Minimum score required for an animation to be considered valid. |
| `iWeightSexStrict` | 100 | Score bonus when actor sex strictly matches position requirement. |
| `iWeightSexLight` | 50 | Score bonus for permissive sex matching (futa/ambiguous cases). |
| `iWeightSexMismatch` | -15 | Score penalty when actor sex doesn't match animation position. |
| `iWeightVampire` | 10 | Score bonus when vampire status matches animation tags. |
| `iWeightSubmissive` | 20 | Score bonus when submissive trait matches animation requirements. |
| `iWeightUnconscious` | 10 | Score bonus when conscious state matches animation requirements. |
| `fScaleTolerance` | 0.1 | Allowed scale deviation from 1.0 for receiving scale bonus. |
| `iWeightScale` | 10 | Score bonus when actor scale is within tolerance of 1.0. |

---

## Creature Race Settings

Boolean toggles to enable/disable specific creature races in animations. Set to `false` to prevent a race from being used in scenes.

<details>
<summary><strong>Click to expand full race list</strong></summary>

| Setting (Race) |
|----------------|
| `bAshHopper` — Ash Hopper |
| `bLurker` — Lurker |
| `bBear` — Bear |
| `bMammoth` — Mammoth |
| `bBoar` — Boar |
| `bMudcrab` — Mudcrab |
| `bBoarMounted` — Mounted Boar |
| `bNetch` — Netch |
| `bBoarSingle` — Single Boar |
| `bRiekling` — Riekling |
| `bCanine` — Canine (generic) |
| `bSabrecat` — Sabrecat |
| `bChaurus` — Chaurus |
| `bSeeker` — Seeker |
| `bChaurusHunter` — Chaurus Hunter |
| `bSkeever` — Skeever |
| `bChaurusReaper` — Chaurus Reaper |
| `bSlaughterfish` — Slaughterfish |
| `bChicken` — Chicken |
| `bSpider` — Spider |
| `bCow` — Cow |
| `bSpriggan` — Spriggan |
| `bDeer` — Deer |
| `bStormAtronach` — Storm Atronach |
| `bDog` — Dog |
| `bTroll` — Troll |
| `bDragon` — Dragon |
| `bVampireLord` — Vampire Lord |
| `bDragonPriest` — Dragon Priest |
| `bWerewolf` — Werewolf |
| `bDraugr` — Draugr |
| `bWisp` — Wisp |
| `bDwarvenBallista` — Dwarven Ballista |
| `bWispmother` — Wispmother |
| `bDwarvenCenturion` — Dwarven Centurion |
| `bWolf` — Wolf |
| `bDwarvenSphere` — Dwarven Sphere |
| `bDwarvenSpider` — Dwarven Spider |
| `bFalmer` — Falmer |
| `bFlameAtronach` — Flame Atronach |
| `bFox` — Fox |
| `bFrostAtronach` — Frost Atronach |
| `bGargoyle` — Gargoyle |
| `bGiant` — Giant |
| `bGiantSpider` — Giant Spider |
| `bGoat` — Goat |
| `bHagraven` — Hagraven |
| `bHare` — Hare |
| `bHorker` — Horker |
| `bHorse` — Horse |
| `bIceWraith` — Ice Wraith |
| `bLargeSpider` — Large Spider |

</details>

---

## Statistics Settings

Settings for NPC sexuality distribution when generating random preferences.

| Setting | Default | Description |
|---------|---------|-------------|
| `fPercentageHetero` | 80.0 | Percentage of NPCs assigned heterosexual preference. |
| `fPercentageHomo` | 9.0 | Percentage of NPCs assigned homosexual preference. |

> **Note:** The remaining percentage (100 - 80 - 9 = 11%) represents bisexual preference.

---

## Distance & Detection Settings

Spatial thresholds used for detecting contact types between actor body parts. Units are game units for distances and degrees for angles.

### General Detection

| Setting | Default | Description |
|---------|---------|-------------|
| `fAnimObjDist` | 23.0 | Maximum distance for animation object attachment. |
| `fDistanceHand` | 8.3 | Distance threshold for hand contact detection. |
| `fDistanceFoot` | 13.3 | Distance threshold for foot-to-body contact. |
| `fDistanceFootMouth` | 4.3 | Distance threshold for foot-to-mouth interaction. |
| `fDistanceMouth` | 5.4 | Distance threshold for mouth/oral contact. |
| `fDistanceCrotch` | 8.0 | Distance threshold for crotch region interaction. |

### Head/Face Orientation

| Setting | Default | Description |
|---------|---------|-------------|
| `fAngleToHeadTolerance` | 20.0 | General angular tolerance for head orientation. |
| `fAngleToHeadSidewaysTolerance` | 50.0 | Angular tolerance when approaching head from side. |
| `fAngleToHeadFrontalTolerance` | 45.0 | Angular tolerance when approaching head from front. |
| `fCloseToHeadRatio` | 1.5 | Distance ratio multiplier for "close to head" checks. |
| `fThroatToleranceRadius` | 0.25 | Radius tolerance for throat/deepthroat detection. |
| `fAdjustHeadLimit` | 33.0 | Maximum allowed head position adjustment (game units). |

### Interaction Angles

| Setting | Default | Description |
|---------|---------|-------------|
| `fAngleCunnilingus` | 130.0 | Angle threshold for cunnilingus positioning. |
| `fAngleKissing` | 70.0 | Maximum angle between faces for kissing detection. |
| `fAngleGrinding` | 70.0 | Angle threshold for grinding contact. |
| `fAngleGrindingFF` | 130.0 | Angle threshold for female-female grinding. |
| `fAnglePenetration` | 90.0 | Maximum angle deviation for valid penetration alignment. |

### Penetration Detection

| Setting | Default | Description |
|---------|---------|-------------|
| `fPenetrationVaginalTolerance` | 1.0 | Distance tolerance for initial vaginal penetration. |
| `fPenetrationVaginalToleranceRepeat` | 3.5 | Looser tolerance for sustained vaginal contact. |
| `fPenetrationAnalToleranceRepeat` | 3.0 | Tolerance for sustained anal contact. |
| `fAdjustSchlongLimit` | 90.0 | Maximum schlong angle adjustment (degrees). |
| `fAdjustSchlongVaginalLimit` | 55.0 | Maximum schlong adjustment for vaginal alignment. |

---

## Enjoyment Settings

Controls the enjoyment/arousal accumulation system during scenes. Enjoyment values are accumulated over time based on detected contact types.

### Enjoyment Rates by Interaction Type

| Setting | Default | Description |
|---------|---------|-------------|
| `fEnjGrinding` | 0.075 | Enjoyment rate multiplier for grinding contact. |
| `fEnjHandActive` | 0.375 | Enjoyment for actor performing hand stimulation. |
| `fEnjHandPassive` | 0.475 | Enjoyment for actor receiving hand stimulation. |
| `fEnjFootActive` | 0.175 | Enjoyment for actor performing foot stimulation. |
| `fEnjFootPassive` | 0.3 | Enjoyment for actor receiving foot stimulation. |
| `fEnjOralActive` | 0.525 | Enjoyment for actor performing oral stimulation. |
| `fEnjOralPassive` | 0.575 | Enjoyment for actor receiving oral stimulation. |
| `fEnjVaginalActive` | 0.725 | Enjoyment for active partner in vaginal. |
| `fEnjVaginalPassive` | 0.825 | Enjoyment for passive partner in vaginal. |
| `fEnjAnalActive` | 0.925 | Enjoyment for active partner in anal. |
| `fEnjAnalPassive` | 1.025 | Enjoyment for passive partner in anal. |

### Enjoyment Modifiers

| Setting | Default | Description |
|---------|---------|-------------|
| `fFactorNonInterEnjRaise` | 0.6 | Multiplier for enjoyment in automatic/AI mode. |
| `fFactorInterEnjRaise` | 1.2 | Multiplier for enjoyment in player-controlled mode. |
| `fTimeMax` | 30.0 | Maximum time (seconds) used in enjoyment curves. |
| `fRequiredXP` | 50.0 | Experience points required for skill level-up. |
| `fBoostTime` | 30.0 | Duration (seconds) of temporary enjoyment boost effects. |
| `fPenaltyTime` | 80.0 | Duration (seconds) of refractory/cooldown penalties. |
| `iMaxNoPainOrgasmsM` | 1 | Maximum orgasms before pain penalties (male actors). |
| `iMaxNoPainOrgasmsF` | 2 | Maximum orgasms before pain penalties (female actors). |

---

## Editing the INI File

To customize these settings:

1. Navigate to your Skyrim installation folder
2. Open `Data\SKSE\Plugins\SexLab.ini`
3. Edit values as desired
4. Save the file
5. Restart Skyrim for changes to take effect

> **Tip:** Back up the original file before making changes so you can restore defaults if needed.

---

## See Also

- [How to Play](../how-to-play/) - MCM configuration and gameplay guide
- [Troubleshooting](../../troubleshooting/) - Common issues and solutions
