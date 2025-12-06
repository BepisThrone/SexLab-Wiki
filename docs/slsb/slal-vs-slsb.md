---
layout: default
title: SLAL vs SLSB
nav_order: 2
parent: SLSB
---

# SLAL vs SLSB

A detailed comparison between the legacy SLAL system and the new SLSB format.

---

## Overview

| Aspect | SLAL | SLSB |
|--------|------|------|
| **Full Name** | SexLab Animation Loader | SexLab Scene Builder |
| **Source Format** | Papyrus scripts (.psc) | JSON files (.json) |
| **Compiled Format** | Papyrus bytecode (.pex) | SexLab Registry (.slr) |
| **Registration** | Runtime via MCM | Automatic at startup |
| **Speed** | Slow (Papyrus-based) | Near-instant (native) |
| **Animation Limit** | 1000 human + 1000 creature | Unlimited |
| **User Action Required** | Yes (MCM clicks) | No |
| **Save Dependency** | Per-save registration | Save-agnostic |

---

## Registration Process

### SLAL Registration

```
Game Start
    ↓
SLAL Initializes (wait)
    ↓
Open MCM → SLAL
    ↓
Select Animation Pack
    ↓
Click "Enable All"
    ↓
Click "Register Animations"
    ↓
Wait for Papyrus to process each animation
    ↓
Repeat for each pack
    ↓
Repeat for each new save
```

**Time:** Minutes per pack, depending on animation count.

### SLSB Registration

```
Game Start
    ↓
SexLab P+ loads .slr (SexLab Registry) files
    ↓
Done!
```

**Time:** Near-instant, regardless of animation count.

---


## Key Differences

### 1. Animation Limits

| System | Human | Creature | Total |
|--------|-------|----------|-------|
| SLAL | 1000 | 1000 | 2000 |
| SLSB | ∞ | ∞ | ∞ |

> **Note:** Legacy mods using `sslBaseAnimation` are still limited to 1000 per type.

### 2. Performance

| Operation | SLAL | SLSB |
|-----------|------|------|
| Registration | Papyrus (slow) | Native (fast) |
| Animation Search | Papyrus (slow) | Native (fast) |
| Scene Startup | Script overhead | Minimal overhead |

### 3. User Experience

| Aspect | SLAL | SLSB |
|--------|------|------|
| Initial Setup | Click through MCM | None |
| New Save | Re-register everything | Just works |
| Adding Packs | Register manually | Restart game |
| Removing Packs | Clean save recommended | Remove and restart |


## Migration Path

### For Users

1. Keep your SLAL packs installed (for meshes/assets)
2. Install SLSB conversion patches on top
3. The conversions contain the SLR files that P+ reads
4. Don't install the SLAL loader itself

### For Pack Authors

1. Use the SLSB conversion tool to convert existing packs
2. Or create new packs directly in SLSB format
3. See [Converting Animations](../converting-animations/) for details

---

## Compatibility

### What Works

- Most mods that start scenes work fine
- Animation tags are preserved
- Event hooks work (scene start, end, stage change)
- Animation filtering by tag

### What Needs Attention

- Mods that register animations via Papyrus need patching
- Voice packs need P+ compatible versions
- Mods checking for specific SLAL functions

---

## Frequently Asked Questions

### Can I use SLAL packs with P+?

Yes, but you need SLSB conversion patches. The SLAL pack provides meshes, the SLSB conversion provides registration data.

### Do I need the SLAL loader?

No. In fact, don't install it with P+.

### Will my favorite pack get converted?

Most popular packs already have conversions. Check [Animation Packs](../../slp/animation-packs/) or the Discord.

### Can I convert packs myself?

Yes! See [Converting Animations](../converting-animations/) for instructions.
