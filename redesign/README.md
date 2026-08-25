# Majlis Redesign — 6 directions

Source photo: the existing majlis / formal living room (long rectangular room,
polished cream marble floor, white coffered ceiling with an ornate ceiling rose
and crystal chandelier, tall recessed-panel walls, dark-framed windows at the far
end, low majlis floor seating along both long walls, deep red Bukhara rug and a
carved hexagonal wooden table at the centre).

Every brief keeps the room's architecture, proportions, camera angle and the
polished marble floor intact, and changes only furniture, textiles, wall finish
and lighting — so all six renders compare directly against the original photo.

v1-v3 are three palettes of one direction (**luxury classic**). v4-v6 are three
separate directions.

## How to run

The Gemini API key is not set in this environment. Set it, then run the three
commands below (each writes a PNG into `~/Documents/nanobanana_generated/`):

```bash
export GOOGLE_AI_API_KEY="<your key from https://aistudio.google.com/apikey>"
SRC=/path/to/majlis-original.jpg
S=/home/user/Na10/.claude/skills/banana/scripts/edit.py

for v in redesign/v*.txt; do python3 "$S" --image "$SRC" --prompt "$(cat "$v")"; done
```

Model: `gemini-3.1-flash-image-preview` (the script's default). `edit.py` exposes
no aspect-ratio or `imageSize` flags — an edit inherits the framing of the source
image, so crop/rotate the source first if you want a different ratio.

Note on orientation: the source JPEG carries EXIF orientation tag 6, so its raw
pixels are 4032x3024 landscape while the intended display is 3024x4032 portrait.
Viewers that ignore EXIF show the room lying on its side. Normalise it before
sending it to the API, otherwise the model renders a sideways room:

```python
from PIL import Image, ImageOps
ImageOps.exif_transpose(Image.open(SRC)).save("source-upright.jpg", quality=95)
```

The three prompts are written for that upright portrait framing.

## The six

### Luxury classic — same direction, three palettes

| | Palette | Lighting |
|---|---|---|
| v1 | Emerald green + antique gold | Evening, chandelier-led warm interior light |
| v2 | Deep garnet + champagne gold | Late-afternoon daylight raking through sheer drapery |
| v3 | Midnight sapphire + antique silver-gold | Blue hour, layered table-lamp and cove lighting |

### Three further directions

| | Direction | Notes |
|---|---|---|
| v4 | Warm modern minimal | Oatmeal boucle platform seating, walnut, chalk-plaster panels, opal glass globe cluster, undyed wool rug. Keeps the majlis layout, strips the ornament. |
| v5 | Contemporary Arabic majlis | Charcoal wool seating with terracotta and ochre cushions, fluted smoked-oak wall paneling with brass reveals, linear brass chandelier, abstracted geometric rug. |
| v6 | Full modern living room | Floor seating removed entirely: greige sectional, cognac leather swivel chairs, marble oval coffee table, walnut console, olive tree, smoked-glass disc chandelier. |
