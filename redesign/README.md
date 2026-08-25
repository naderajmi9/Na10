# Majlis Redesign — Luxury Classic (3 variations)

Source photo: the existing majlis / formal living room (long rectangular room,
polished cream marble floor, white coffered ceiling with an ornate ceiling rose
and crystal chandelier, tall recessed-panel walls, dark-framed windows at the far
end, low majlis floor seating along both long walls, deep red Bukhara rug and a
carved hexagonal wooden table at the centre).

Direction chosen: **Luxury classic** — lean into the existing formality with
jewel-toned silks and velvets, gilded moldings, a statement crystal chandelier
and heavy drapery, while keeping the room's architecture, proportions and camera
angle intact.

## How to run

The Gemini API key is not set in this environment. Set it, then run the three
commands below (each writes a PNG into `~/Documents/nanobanana_generated/`):

```bash
export GOOGLE_AI_API_KEY="<your key from https://aistudio.google.com/apikey>"
SRC=/path/to/majlis-original.jpg
S=/home/user/Na10/.claude/skills/banana/scripts/edit.py

python3 "$S" --image "$SRC" --prompt "$(cat redesign/v1-emerald-gold.txt)"
python3 "$S" --image "$SRC" --prompt "$(cat redesign/v2-garnet-champagne.txt)"
python3 "$S" --image "$SRC" --prompt "$(cat redesign/v3-sapphire-silver.txt)"
```

Model: `gemini-3.1-flash-image-preview` (the script's default). `edit.py` exposes
no aspect-ratio or `imageSize` flags — an edit inherits the framing of the source
image, so crop/rotate the source first if you want a different ratio.

Note: the source file is stored rotated 90° (portrait bytes, landscape scene).
Each prompt tells the model to render the room upright in landscape orientation.

## What varies between the three

| | Palette | Lighting |
|---|---|---|
| v1 | Emerald green + antique gold | Evening, chandelier-led warm interior light |
| v2 | Deep garnet + champagne gold | Late-afternoon daylight raking through sheer drapery |
| v3 | Midnight sapphire + antique silver-gold | Blue hour, layered table-lamp and cove lighting |
