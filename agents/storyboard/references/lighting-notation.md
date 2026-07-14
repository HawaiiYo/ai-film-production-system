# Lighting Notation System (光线指示系统)

Storyboard light source direction and type notation, for cinematographer and gaffer to set up lighting accordingly.

## 1. Light Source Direction Notation

```
+--------------------------------------------------+
|            Light Direction Notation Symbols        |
+---------------+----------+-------------------------+
|  Notation     |  Symbol   |  Meaning                 |
+---------------+----------+-------------------------+
| Key Light     | [solid] arrow  |  Main light source direction  |
| (Key)         | (thick arrow)  |  Primary light source in frame |
+---------------+----------+-------------------------+
| Fill Light    | [hollow] arrow |  Fill light direction          |
| (Fill)        | (thin arrow)   |  Secondary light filling shadows|
+---------------+----------+-------------------------+
| Backlight     | <-[solid] tail|  Backlight / Rim light          |
| (Back)        | behind subject |  Light from behind, outlining subject |
+---------------+----------+-------------------------+
| Rim Light     | [solid]^ side  |  Rim light / Hair light         |
| (Rim)         | (thin notation)|  Light from side-rear           |
+---------------+----------+-------------------------+
| Practical     | (lightbulb) icon| Visible practical source in frame|
| (Practical)   |                |  Lamp / candle / screen / neon  |
+---------------+----------+-------------------------+
| Ambient       | .... dashed    |  Ambient light (no clear direction)|
| (Ambient)     | surrounding    |  Overall atmosphere light        |
+---------------+----------+-------------------------+
| Bounce        | angled broken  |  Bounced light                  |
| (Bounce)      | line           |  Light reflected from walls/floor onto subject |
+---------------+----------+-------------------------+
```

### Storyboard Lighting Notation Example

```
+--------------------------------------+
| S4-003  CU  85mm  f/2.0  4s        |
| [LIGHT] KEY: ->> (window key, right) |
| [LIGHT] FILL: -> (soft bounce, front-left) |
| [LIGHT] RIM: ^ (backlight, top-rear) |
| [COLOR TEMP] 3200K warm (key) + cool blue (back) |
|                                      |
|        [RIM ^]                        |
|    +--------------+                  |
|    |  [CHAR FACE] | <-(soft fill)     |
|    |  half-bright |                  |
|    |  half-dark   |                  |
|    |  (Rembrandt  |                  |
|    |   Lighting)  |                  |
|    +--------------+                  |
|         ^^                           |
|     (window key)                     |
+--------------------------------------+
```

## 2. Common Lighting Style Notation

| Lighting Style | Notation | Characteristics | Best Use |
|---------------|----------|-----------------|----------|
| Rembrandt Lighting | `[LIGHT] REMBRANDT` | Triangular cheek light patch | Portrait / deep character |
| Split Lighting | `[LIGHT] SPLIT` | Half face lit, half dark | Conflict / dual personality |
| Loop Lighting | `[LIGHT] LOOP` | Small shadow beside nose | General flattering |
| Butterfly Lighting | `[LIGHT] BUTTERFLY` | Butterfly-shaped shadow under nose | Beauty / glamour |
| Silhouette | `[LIGHT] SILHOUETTE` | Pure silhouette | Suspense / mystery |
| Low-Key | `[LIGHT] LOW-KEY` | Large areas of darkness | Film noir / thriller |
| High-Key | `[LIGHT] HIGH-KEY` | Large areas of brightness | Comedy / commercial |
| Practical Only | `[LIGHT] PRACTICAL` | Only in-frame source lighting | Realism / natural feel |