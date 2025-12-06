---
layout: default
title: Why P+?
nav_order: 3
parent: SexLab P+
---

# Why Choose SexLab P+?

Already using vanilla SexLab and wondering why you should switch? This guide explains the improvements and answers common migration concerns.

---

## The Problems with Vanilla SexLab

Vanilla SexLab, while revolutionary for its time, has significant limitations:

### Performance Issues
- **Slow animation registration** - Loading animations takes a long time
- **Scene startup delays** - Noticeable pauses when starting scenes
- **Script lag** - Heavy Papyrus load during scenes

### Technical Limitations
- **1000 animation cap** - Can't register more than 1000 human + 1000 creature animations
- **Manual registration** - Must register animations through MCM each game
- **Settings tied to saves** - MCM settings don't persist across saves

### Maintenance
- **Requires addon mods** - Need SLSO, SLAS, etc. for common features
- **Outdated codebase** - Harder for mod authors to work with

---

## What P+ Fixes

### 🚀 Extreme Performance

| Operation | Vanilla SL | SexLab P+ |
|-----------|-----------|-----------|
| Animation Registration | Minutes | Near-instant |
| Scene Startup | Noticeable delay | Immediate |
| Animation Search | Slow | Extremely fast |

P+ completely rewrites the registration and animation systems for modern performance.

### 📈 Unlimited Animations

No more hitting the 1000 animation wall. P+ removes the cap entirely.

> **Note:** Mods using the legacy API (sslBaseAnimation) are still limited to accessing the first 1000 animations. Most modern mods work with the full library.

### ⚙️ Automatic Everything

- **Auto-registration** - Animations register at game startup, no MCM clicking
- **Persistent settings** - MCM configuration is save-agnostic and auto-loads
- **No maintenance** - Set it up once, forget about it

### 🔧 Built-in Features

P+ includes functionality that previously required separate mods:

| Built Into P+ | Previously Required |
|---------------|---------------------|
| Separate Orgasm logic | SLSO |
| Fast animation search | SLAS |
| Grass clipping fix | SLGP |
| Smooth expressions | SL Smooth Expressions |

---

## Common Migration Concerns

### "My current setup works fine"

It probably does! But you may not realize what you're missing:

- You might be experiencing script lag you've normalized
- Your animation slots might be nearly full
- You're maintaining multiple mods that P+ consolidates

### "Will my other mods break?"

**Most mods work fine.** P+ maintains backwards compatibility for:
- Scene detection events
- API calls for starting scenes
- Animation tags and filtering

See [Incompatible Mods](../incompatible-mods/) for the known exceptions.

### "What about my animations?"

Your SLAL packs will need **SLSB conversion patches**. The good news:
- Most popular packs already have conversions available
- The conversion process is automated for pack developers
- You install both the original pack (for meshes) and the conversion patch

### "Will I lose my MCM settings?"

P+ uses a different settings system, so you'll need to reconfigure. However, once set up, your settings persist across all saves automatically.

---

## What You Gain

✅ **Performance** - Dramatically faster in all operations  
✅ **Capacity** - Unlimited animation slots  
✅ **Simplicity** - Fewer mods to manage  
✅ **Modern features** - Rebuilt enjoyment/orgasm system  
✅ **Active development** - Regular updates and support  
✅ **Future-proof** - New animations release in SLSB format  

---

## What You Might Lose

⚠️ **Some mod compatibility** - A few older mods don't work (see [Incompatible Mods](../incompatible-mods/))  
⚠️ **Voice pack compatibility** - New voice engine requires P+ compatible packs  
⚠️ **SLAL direct support** - Need conversion patches for animation packs  

---

## Migration Checklist

1. ✅ Backup your current setup (MO2 profile or Vortex snapshot)
2. ✅ Check your critical mods against the [compatibility list](../incompatible-mods/)
3. ✅ Download SLSB conversion patches for your animation packs
4. ✅ Follow the [Installation Guide](../installation/)
5. ✅ Test on a new save first

---

## Still Unsure?

See the full [Feature Comparison](../comparison/) table, or join the [Discord](https://discord.gg/JPSHb4ebqj) to ask questions.
