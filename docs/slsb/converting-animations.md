---
layout: default
title: Converting Animations
permalink: /slsb/converting-animations/
---

# Converting Animations

How to convert SLAL animation packs to SLSB format for SexLab P+.

---

## Overview

Converting SLAL packs to SLSB involves:

1. Extracting animation data from SLAL source files
2. Converting to JSON format
3. Compiling JSON to `.slr` (SexLab Registry) files using SLSB
4. Packaging for distribution

There are tools available to automate most of this process.

---

## Prerequisites

Before you start, you'll need:

- The original SLAL animation pack
- Python 3.8+ (for the conversion script)
- Basic understanding of the command line
- The SLSB conversion tools

---

## Quick Conversion Guide

### Step 1: Get the Tools

Download the conversion tools from:
- [Discord #slsb-and-pack-dev channel](https://discord.gg/JPSHb4ebqj)
- [MissCorruption's Tutorial](https://gist.github.com/MissCorruption/fc62e0b46e3652ad6a85fe903a6a9b37)

### Step 2: Locate SLAL Source

Find the SLAL source file for your animation pack. It's usually at:
```
Data/Source/Scripts/SLAL_PackName.psc
```

### Step 3: Run the Converter

```bash
python slsb_convert.py SLAL_PackName.psc -o output/
```

### Step 4: Compile with SLSB

Run the SLSB tool to compile your JSON into `.slr` files:
```bash
slsb build PackName.json -o Data/SKSE/Plugins/SexLabRegistry/
```

This generates `PackName.slr` which P+ will load.

### Step 5: Verify Output

Check the generated `.slr` files in the output directory:
```
Data/SKSE/Plugins/SexLabRegistry/PackName.slr
```

### Step 6: Test

1. Install the original SLAL pack (for meshes)
2. Install your compiled `.slr` files
3. Start the game and verify animations appear

---

## Detailed Conversion Process

### Understanding SLAL Structure

An SLAL pack typically contains:

```
MyAnimPack/
├── meshes/
│   └── actors/
│       └── character/
│           └── animations/
│               └── MyAnims/
│                   ├── anim001_s1_a0.hkx
│                   ├── anim001_s1_a1.hkx
│                   └── ...
├── Source/
│   └── Scripts/
│       └── SLAL_MyAnimPack.psc
└── scripts/
    └── SLAL_MyAnimPack.pex
```

### Key Data to Extract

From each animation definition:
- **Name** - Display name
- **ID** - Unique identifier
- **Tags** - Categories (Aggressive, Loving, etc.)
- **Actor count** - Number of participants
- **Gender tags** - Actor genders
- **Creature info** - Race keys for creature animations
- **Stage data** - Animation file references per stage
- **Positioning** - Actor positions and rotations

### SLSB Output Format

The converter produces JSON files like:

```json
{
  "animations": [
    {
      "name": "Animation Display Name",
      "id": "UniqueAnimID",
      "tags": ["Tag1", "Tag2", "Tag3"],
      "sound": "default",
      "actors": [
        {
          "gender": "male",
          "race": "human",
          "add_cum": 0
        },
        {
          "gender": "female",
          "race": "human",
          "add_cum": 1
        }
      ],
      "stages": [
        {
          "id": "stage1",
          "timer": 30.0,
          "tags": [],
          "positions": [
            {
              "event": "anim_s1_a0",
              "offset": [0.0, 0.0, 0.0, 0.0]
            },
            {
              "event": "anim_s1_a1",
              "offset": [0.0, 50.0, 0.0, 180.0]
            }
          ]
        }
      ]
    }
  ]
}
```

---

## Manual Adjustments

Sometimes automated conversion needs manual fixes:

### Common Issues

| Issue | Solution |
|-------|----------|
| Missing tags | Add tags manually to JSON |
| Wrong positions | Adjust offset values |
| Stage timing | Modify timer values |
| Incorrect genders | Fix gender fields |

### Tag Guidelines

Common tags for proper categorization:

| Tag | Meaning |
|-----|---------|
| Aggressive | Non-consensual theme |
| Loving | Romantic/gentle |
| Oral | Oral interaction |
| Anal | Anal interaction |
| Vaginal | Vaginal interaction |
| Masturbation | Solo activity |
| Foreplay | Non-penetrative |
| FF, MF, MM | Gender combination |

---

## Creature Animations

Creature animations need additional data:

```json
{
  "actors": [
    {
      "gender": "female",
      "race": "human"
    },
    {
      "gender": "creature",
      "race": "wolf",
      "race_key": "Wolves"
    }
  ]
}
```

### Race Keys

Common race keys:
- `Wolves` - Wolves, dogs
- `Bears` - Bears
- `Trolls` - Trolls
- `Giants` - Giants
- `Spiders` - Frostbite spiders
- `Draugrs` - Draugr
- `Falmer` - Falmer
- `Rieklings` - Rieklings
- `Dragons` - Dragons

---

## Testing Your Conversion

### Quick Test

1. Start a new game (or use a test save)
2. Open console (`~`)
3. Check for your animations in the SL MCM
4. Try starting a scene with your animations

### Debugging

If animations don't appear:
- Check JSON syntax before compiling (use a JSON validator)
- Verify `.slr` file location (`Data/SKSE/Plugins/SexLabRegistry/`)
- Check Papyrus logs for errors
- Ensure mesh files (.hkx) are in correct location

---

## Distribution

### Package Structure

Your conversion package should contain:
```
MyPack_SLSB_Conversion/
└── Data/
    └── SKSE/
        └── Plugins/
            └── SexLabRegistry/
                └── MyPack.slr
```

### Documentation

Include a README noting:
- Required base pack (SLAL version)
- Installation order
- Any known issues
- Credits to original author

### Permissions

Always check the original pack's permissions before distributing conversions. Many authors require permission for derivative works.

---

## Getting Help

- **Discord**: [#slsb-and-pack-dev](https://discord.gg/JPSHb4ebqj)
- **Tutorial**: [MissCorruption's Guide](https://gist.github.com/MissCorruption/fc62e0b46e3652ad6a85fe903a6a9b37)
- **Examples**: Check existing converted packs for reference
