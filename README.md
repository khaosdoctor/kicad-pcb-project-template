# KiCad PCB Project Template

A GitHub template repository for new KiCad PCB projects with automated CI/CD using [KiBot](https://github.com/INTI-CMNB/KiBot).

## Usage

1. Click **"Use this template"** on GitHub to create a new repository.
2. Rename your KiCad project files to `project.kicad_pcb` and `project.kicad_sch` (or update the `board` and `schema` fields in `.github/workflows/kibot.yml` to match your filenames).
3. Customize `kibot.yaml` if needed (e.g., add LCSC part numbers for JLCPCB assembly).
4. Push to `main` — the CI workflow will automatically generate manufacturing files, documentation, BOM, and 3D renders.

## What the CI does

On every push to `main` and on pull requests, the [KiBot GitHub Action](https://github.com/INTI-CMNB/KiBot) runs and produces:

| Output | Location |
|--------|----------|
| Gerbers + drill files | `Manufacturing/Gerbers/` |
| Pick-and-place (CPL) | `Manufacturing/Assembly/` |
| Bill of Materials (CSV) | `Manufacturing/Assembly/` |
| JLCPCB BOM | `Manufacturing/Assembly/` |
| Zipped manufacturing package | `Manufacturing/` |
| Schematic PDF | `Documentation/` |
| PCB layers PDF | `Documentation/` |
| Interactive HTML BOM | `bom/` |
| STEP 3D model | `3D/` |
| 3D renders (top & bottom) | `3D/` |

On pushes to `main`, the interactive BOM and 3D renders are automatically committed back to the repository.

All outputs are also uploaded as a GitHub Actions artifact named `kibot-outputs`.

## Requirements

- KiCad 8/9 project files (`.kicad_pcb`, `.kicad_sch`)
- No local KiBot installation needed — everything runs in CI via Docker
