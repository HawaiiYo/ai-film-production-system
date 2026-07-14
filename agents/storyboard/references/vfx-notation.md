# VFX & Effects Notation System (FX与特效标注系统)

When a shot involves visual effects (CGI / compositing / particles, etc.), the boundary between practical and post-production must be clearly marked on the storyboard.

## 1. VFX Notation Symbols

```
+--------------------------------------------------+
|            FX Notation Symbol System               |
+---------------+----------+-------------------------+
|  Notation     |  Representation |  Meaning              |
+---------------+----------+-------------------------+
| CGI Element   | .... dashed box | Element requiring CGI generation |
| (CGI)         | + CGI label     |                          |
+---------------+----------+-------------------------+
| Green Screen  | [block] color   | Green/blue screen area (replaced in post) |
| (GS)          | + GS label      |                          |
+---------------+----------+-------------------------+
| Particle FX   | *** star points | Particle effects (smoke/fire/dust/snow) |
| (Particle)    | + Particle label|                          |
+---------------+----------+-------------------------+
| Compositing   | [  ] brackets   | Composite layers (multi-layer combined) |
| Layer (Comp)  | + L1/L2 label   |                          |
+---------------+----------+-------------------------+
| Motion Track  | +++ cross marks | Motion tracking points    |
| (Track)       | + Track label   |                          |
+---------------+----------+-------------------------+
| Practical FX  | [lightning] icon| Practical effects (explosions/rain/wind) |
| (Prac FX)     | + Prac FX label |                          |
+---------------+----------+-------------------------+
| Light Effect  | glitter rays    | Light effects (lens flare/laser/magic) |
| (Light FX)    | + Light FX label|                          |
+---------------+----------+-------------------------+
| Transition FX | squiggle transition | Frame dissolve/particle fade transition |
| (Trans FX)    | + Trans FX label|                          |
+---------------+----------+-------------------------+
```

### VFX Storyboard Notation Example

```
+--------------------------------------+
| S5-007  LS  24mm  VFX SHOT  8s     |
| [WARNING] This shot contains VFX, requires post compositing |
|                                      |
|         [Sky: CGI block]             |
|    +------------------------+       |
|    |  (clouds) CGI: Giant starship | |
|    |      slowly descending        | |
|    |                        |       |
|    |  [city] [Practical: City skyline] | |
|    |  [crowd] [Practical: Crowd looking up] | |
|    |  L1: Foreground crowd    |       |
|    +------------------------+       |
|                                      |
|  Composite Layers:                    |
|  L3 (farthest): CGI starship + volumetric light |
|  L2: CGI sky replacement + atmospheric haze |
|  L1: Practical city skyline + foreground crowd |
|                                      |
|  Track Points: (+) 3 tracking markers on building tops |
|  Light FX: [glitter] Starship engine glow (post) |
|  Particles: [stars] Atmospheric dust (post) |
+--------------------------------------+
```

## 2. AI Video Generation FX Descriptions

```
Additional keywords to include in Seedance Prompt:

1. CGI / Compositing Elements:
   "composited with CGI starship descending from clouds"

2. Particle Effects:
   "particle effects: dust, smoke, sparks, debris floating in air"

3. Light Effects:
   "lens flare, volumetric light rays, glowing energy effects"

4. Green Screen / Background Replacement:
   "green screen background to be replaced with [scene] in post"

5. Negative Prompt additions:
   "no inconsistent lighting between foreground and background,
    no edge artifacts around composited elements"
```