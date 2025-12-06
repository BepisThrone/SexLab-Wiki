---
layout: default
title: Introduction
nav_order: 1
parent: SLSB
---

# SexLab Scene Builder (SLSB)

SLSB is an external tool and the next-generation animation registration system for SexLab P+.

---

## What is SLSB?

**SexLab Scene Builder** is an external tool that replaces SLAL (SexLab Animation Loader) as the method for registering animations with SexLab P+. It compiles JSON animation definitions into `.slr` (SexLab Registry) files that P+ reads at startup.

It provides:

- **Instant registration** - No manual MCM clicking
- **No animation cap** - Unlimited animations
- **Better organization** - More structured animation data
- **Simpler format** - JSON-based configuration
- **Compiled output** - JSON → .slr files for optimal loading

---

## Why SLSB?

### Problems with SLAL

SLAL has served the community well, but has limitations:

| Issue | Description |
|-------|-------------|
| Slow registration | Animations register one-by-one through Papyrus |
| Animation cap | Hard limit of 1000 human + 1000 creature |
| Manual process | Users must click through MCM to register |
| Save dependency | Registrations are per-save |
| Papyrus overhead | Heavy script load during registration |

### SLSB Improvements

| Improvement | Description |
|-------------|-------------|
| Instant loading | Animations load at game start |
| No limits | Register unlimited animations |
| Automatic | No user interaction required |
| Save-agnostic | Works across all saves |
| Native performance | Handled by SKSE, not Papyrus |

---

## How It Works

### SLAL Workflow (Old)

1. Install animation pack with SLAL files
2. Start game, wait for SLAL to initialize
3. Open MCM → SLAL → Select pack
4. Click "Register" and wait
5. Repeat for each pack
6. Repeat for each save game

### SLSB Workflow (New)

1. Install animation pack containing `.slr` files
2. Start game
3. Done! P+ loads the registry files automatically

### For Pack Authors

1. Create/edit JSON animation definitions
2. Run SLSB tool to compile JSON → `.slr`
3. Distribute the `.slr` files to users

---

## File Structure

SLSB uses JSON source files that compile to `.slr` registry files:

### SLAL Structure (Old)
```
Data/
└── Source/Scripts/
    └── SLAL_MyAnimPack.psc      # Papyrus source
└── Scripts/
    └── SLAL_MyAnimPack.pex      # Compiled script
```

### SLSB Structure (New)
```
Source (development):
└── MyAnimPack.json              # JSON definition (author keeps this)

Distributed to users:
Data/
└── SKSE/Plugins/SexLabRegistry/
    └── MyAnimPack.slr           # Compiled registry file
```

> **Note:** Users install the compiled `.slr` files. Pack authors work with JSON and use SLSB to compile them.

---

## Getting Started

### For Users

If you just want to use animation packs:

1. Install SLSB-compatible packs (or SLAL packs with SLSB conversions)
2. That's it! They work automatically.

See [Animation Packs](../../slp/animation-packs/) for available packs.

### For Developers

If you want to create or convert animation packs:

1. [SLAL vs SLSB](../slal-vs-slsb/) - Understand the differences
2. [Converting Animations](../converting-animations/) - Convert existing SLAL packs
3. [Environment Setup](../environment-setup/) - Set up your development tools

---

## Resources

- **Discord**: [Join for support](https://discord.gg/JPSHb4ebqj) - #slsb-and-pack-dev channel
- **GitHub**: [SexLab Source](https://github.com/Scrabx3/SexLab)
- **Conversion Tutorial**: [MissCorruption's Guide](https://gist.github.com/MissCorruption/fc62e0b46e3652ad6a85fe903a6a9b37)
