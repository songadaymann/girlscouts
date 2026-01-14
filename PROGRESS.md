# Girl Scout Cookie Order Game - Progress

## Overview
A mobile-first game to help practice filling Girl Scout cookie orders. Based on the real-world experience of pulling boxes from a car trunk and stacking them on a pallet for customers.

## Core Gameplay
1. **Order Form Phase**: Player sees a simplified order form with a funny customer name and list of cookies/quantities
2. **Memorization**: Player studies the order and hits "MEMORIZE & START!"
3. **Filling Phase**: Order form disappears, timer starts - player must fill the order from memory
4. **Drag & Drop**: Drag cookie boxes from the car trunk to the pallet
5. **Physics Stacking**: Boxes stack realistically using Matter.js physics
6. **Completion**: Hit "DONE!" to check the order - shows results and tracks stats

## Features Implemented

### Visual Assets
- [x] Parking lot background (`assets/parkinglot.jpg`)
- [x] Car with open trunk (`assets/car.png`)
- [x] Wooden pallet (`assets/palette.png`)
- [x] All 9 cookie box sprites (`assets/sprites/cookieBoxes/`)
  - Thin Mints, Samoas, Tagalongs, Do-Si-Dos, Trefoils
  - Lemon-Ups, Adventurefuls, Exploreamores, Toffee-tastic

### Girl Scout Branding
- [x] Palatino font (official GS brand font)
- [x] Girl Scout Green (#00b451) accent color
- [x] White backgrounds with green borders on modals
- [x] Color swatches extracted from actual sprite images
- [x] Clean, professional styling throughout

### Game Mechanics
- [x] Funny random name generator for customers
  - Combines titles (Mrs., Dr., Professor, etc.)
  - Funny first names (Barnaby, Winifred, Cornelius, etc.)
  - Funny last names (Wigglebottom, Snickerdoodle, Bananapants, etc.)
- [x] Random order generation (2-5 cookie types, 1-4 boxes each)
- [x] Drag and drop from trunk to pallet
- [x] Matter.js physics for realistic box stacking
- [x] Click boxes on pallet to remove them (fix mistakes)
- [x] Order validation (checks correct cookies and quantities)
- [x] Timer (per-order timing)
- [x] "See Order" button to peek at current order during gameplay

### Physics System
- [x] Per-cookie physics colliders (different sizes for horizontal vs vertical boxes)
- [x] Pallet acts as a "box" container (walls on left, right, bottom - open top)
- [x] Screen boundaries to catch any escaping boxes
- [x] Reduced bounce/restitution for stable stacking
- [x] Air friction for smoother box settling

### HUD Modal
Consolidated stats display centered at top of screen:
- [x] Orders completed count
- [x] Current order timer
- [x] Best time record
- [x] "See Order" button (appears during filling phase)

### Stats Tracking
- [x] Orders completed (successful only)
- [x] Current order timer
- [x] Best single order time

### Editor Mode
Full position editor accessible via "EDITOR" button:

**Car Position**
- Left %, Bottom %, Width %

**Pallet Position**
- Right %, Bottom %, Width %

**Physics Colliders**
- Ground Y % (where boxes land on pallet)
- Wall Inset % (invisible side walls)
- Wall Height (how high boxes can stack)

**Global Box Size**
- Width px, Height px (visual size of all boxes)

**Individual Cookie Settings**
- Left % and Bottom % (position in trunk)
- Phys W and Phys H (physics collider size per cookie)
- Red debug overlay shows physics bounds in editor mode

**Export/Import**
- Export to JSON
- Copy to clipboard
- Reset to defaults
- `loadLayout(json)` function in console

### Current Layout Settings
```json
{
  "car": {
    "left": -3,
    "bottom": 9,
    "width": 59
  },
  "pallet": {
    "right": 5,
    "bottom": 5,
    "width": 35
  },
  "collider": {
    "groundY": 51,
    "wallInset": 10,
    "wallHeight": 200
  },
  "globalBoxSize": {
    "width": 110,
    "height": 98
  },
  "boxes": {
    "thinmints": { "left": 17, "bottom": 33, "physicsWidth": 113, "physicsHeight": 61 },
    "samoas": { "left": 15, "bottom": 41, "physicsWidth": 57, "physicsHeight": 98 },
    "tagalongs": { "left": 24, "bottom": 33, "physicsWidth": 108, "physicsHeight": 51 },
    "dosidos": { "left": 19, "bottom": 41, "physicsWidth": 60, "physicsHeight": 98 },
    "trefoils": { "left": 24, "bottom": 39, "physicsWidth": 110, "physicsHeight": 72 },
    "lemonups": { "left": 30, "bottom": 33, "physicsWidth": 110, "physicsHeight": 63 },
    "adventurefuls": { "left": 30, "bottom": 39, "physicsWidth": 110, "physicsHeight": 62 },
    "smores": { "left": 24, "bottom": 47, "physicsWidth": 59, "physicsHeight": 98 },
    "toffeetastic": { "left": 30, "bottom": 47, "physicsWidth": 43, "physicsHeight": 98 }
  }
}
```

### Cookie Colors (extracted from sprites)
| Cookie | Color | Hex |
|--------|-------|-----|
| Thin Mints | Green | #008c3c |
| Samoas | Purple | #501464 |
| Tagalongs | Red | #dc2814 |
| Do-Si-Dos | Orange | #dc7814 |
| Trefoils | Blue | #0064b4 |
| Lemon-Ups | Yellow | #f0c800 |
| Adventurefuls | Tan | #dcc8a0 |
| Exploreamores | Pink | #dc7878 |
| Toffee-tastic | Teal | #28a0a0 |

### Responsive Design
- [x] Landscape-only orientation
- [x] "Turn your device sideways" message for portrait mode
- [x] Touch-friendly drag and drop
- [x] Works on mobile/tablet
- [x] **Fully responsive cookie sizes** - scales with viewport width
- [x] **Responsive physics colliders** - scale proportionally with visual sizes
- [x] **Dynamic resize handling** - boxes maintain relative positions when viewport changes
- [x] Scale factor based on reference width (1920px)
- [x] Debounced resize handler for performance
- [x] Scale indicator in editor showing current scale %

## Tech Stack
- Vanilla HTML/CSS/JavaScript
- Matter.js for physics
- Palatino font family
- No build process required - just open index.html

## File Structure
```
girlscout/
├── index.html          # Main game file (all-in-one)
├── PROGRESS.md         # This file
└── assets/
    ├── car.png
    ├── palette.png
    ├── parkinglot.jpg
    └── sprites/
        └── cookieBoxes/
            ├── thinmints.png
            ├── samoas.png
            ├── tagalongs.png
            ├── dosidos.png
            ├── trefoils.png
            ├── lemonups.png
            ├── adventurfuls.png
            ├── exploreamores.png
            └── toffe-tastic.png
```

### Sound Effects
- [x] Background music (GirlscoutCookies.mp3) - loops continuously
- [x] Pickup sound when grabbing a cookie box
- [x] Putdown sound when dropping on pallet
- [x] Success sound (yay!) when order is correct
- [x] Fail sound (ohno) when order is wrong

### Welcome/Tutorial Screen
- [x] Shows on first load explaining how to play
- [x] "LET'S GO!" button starts the game and music
- [x] Clear instructions: memorize order, drag boxes, hit done

## Future Ideas / TODO
- [ ] Difficulty progression (more cookies, larger quantities)
- [ ] High score persistence (localStorage)
- [ ] Multiple game modes
- [ ] Leaderboard
- [ ] Animations for success/failure
- [ ] Time bonuses/penalties
