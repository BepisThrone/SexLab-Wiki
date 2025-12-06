---
layout: default
title: Environment Setup
nav_order: 4
parent: SLSB
---

# Environment Setup

Set up your development environment for creating and converting SLSB animation packs.

---

## Required Software

### Python

SLSB conversion tools require Python 3.8 or higher.

#### Windows

1. Download from [python.org](https://www.python.org/downloads/)
2. Run the installer
3. **Important:** Check "Add Python to PATH"
4. Click "Install Now"

Verify installation:
```powershell
python --version
```

#### Alternative: Using Scoop (Windows)

```powershell
scoop install python
```

### Text Editor

You'll need a good text editor for JSON files:

| Editor | Notes |
|--------|-------|
| [VS Code](https://code.visualstudio.com/) | Recommended - great JSON support |
| [Notepad++](https://notepad-plus-plus.org/) | Lightweight alternative |
| [Sublime Text](https://www.sublimetext.com/) | Fast and feature-rich |

#### VS Code Extensions

Recommended extensions for SLSB development:
- **JSON Tools** - JSON formatting and validation
- **Prettier** - Code formatter
- **Error Lens** - Inline error display

---

## Conversion Tools

### Getting the Tools

1. Join the [Discord](https://discord.gg/JPSHb4ebqj)
2. Go to #slsb-and-pack-dev channel
3. Check pinned messages for the latest tools

### Tool Contents

The toolkit typically includes:

```
slsb-tools/
├── slsb                    # SLSB compiler (generates .slr files)
├── slsb_convert.py         # SLAL to JSON conversion script
├── slsb_validate.py        # JSON validator
├── templates/              # Template files
│   ├── animation.json
│   └── pack.json
├── examples/               # Example conversions
└── README.md
```

### Installing Dependencies

```bash
cd slsb-tools
pip install -r requirements.txt
```

If there's no requirements.txt, the script likely uses only standard library.

---

## Project Structure

### Recommended Layout

```
MyAnimationProject/
├── source/
│   └── SLAL_Original.psc    # Original SLAL source (reference)
├── json/
│   └── MyPack.json          # Your JSON definitions
├── output/
│   └── Data/
│       └── SKSE/
│           └── Plugins/
│               └── SexLabRegistry/
│                   └── MyPack.slr   # Compiled registry
├── tools/
│   ├── slsb                 # SLSB compiler
│   └── slsb_convert.py
└── README.md
```

### Output Structure

Your final package for users should contain:
```
Data/
└── SKSE/
    └── Plugins/
        └── SexLabRegistry/
            └── YourPack.slr
```

> **Note:** Users only need the compiled `.slr` files. Keep your JSON sources for future edits.

---

## Setting Up Your First Conversion

### Step 1: Create Project Folder

```bash
mkdir my-slsb-project
cd my-slsb-project
mkdir source json output tools
```

### Step 2: Copy Tools

Copy the conversion tools to your `tools/` folder.

### Step 3: Get SLAL Source

Find the original SLAL source file (`.psc`) and copy to `source/`.

Location is usually:
```
[Mod]\Data\Source\Scripts\SLAL_PackName.psc
```

### Step 4: Convert SLAL to JSON

```bash
python tools/slsb_convert.py source/SLAL_PackName.psc -o json/
```

### Step 5: Compile JSON to SLR

```bash
tools/slsb build json/PackName.json -o output/Data/SKSE/Plugins/SexLabRegistry/
```

This produces the `.slr` file that users will install.

---

## JSON Validation

### Using the Validator

```bash
python slsb_validate.py json/MyPack.json
```

### Online Validators

You can also use online JSON validators:
- [JSONLint](https://jsonlint.com/)
- [JSON Formatter](https://jsonformatter.curiousconcept.com/)

### Common JSON Errors

| Error | Cause | Fix |
|-------|-------|-----|
| Unexpected token | Missing comma | Add comma between elements |
| Unterminated string | Missing quote | Close string with " |
| Invalid character | Special characters | Escape or remove |
| Trailing comma | Comma after last item | Remove trailing comma |

---

## Testing Environment

### Game Setup

For testing conversions:

1. **Separate Profile**: Create a dedicated MO2/Vortex profile for testing
2. **Minimal Setup**: Only essential mods + SL P+ + your conversion
3. **Test Save**: Keep a clean save for quick testing

### Quick Test Process

1. Install your conversion
2. Launch game, load test save
3. Open MCM → SexLab
4. Check if animations appear
5. Test with console commands or MatchMaker

### Debugging

Enable Papyrus logging to catch errors:

`skyrim.ini`:
```ini
[Papyrus]
bEnableLogging=1
bEnableTrace=1
```

Check logs at:
```
Documents/My Games/Skyrim Special Edition/Logs/Script/
```

---

## Version Control

### Using Git

Recommended for tracking changes:

```bash
git init
git add .
git commit -m "Initial conversion"
```

### .gitignore

```gitignore
# Ignore compiled files
*.pex

# Ignore game files
*.bsa
*.hkx

# Ignore personal notes
notes.txt
TODO.txt
```

---

## Batch Processing

### Converting Multiple Packs

Create a batch script for multiple packs:

**Windows (batch):**
```batch
@echo off
for %%f in (source\*.psc) do (
    python tools\slsb_convert.py "%%f" -o output\
)
echo Done!
```

**PowerShell:**
```powershell
Get-ChildItem source\*.psc | ForEach-Object {
    python tools\slsb_convert.py $_.FullName -o output\
}
```

---

## Additional Resources

- **Discord**: [#slsb-and-pack-dev](https://discord.gg/JPSHb4ebqj) for help
- **Tutorial**: [MissCorruption's Guide](https://gist.github.com/MissCorruption/fc62e0b46e3652ad6a85fe903a6a9b37)
- **GitHub**: [SexLab Repository](https://github.com/Scrabx3/SexLab) for source reference
