# 180-Degree Rule & Eyeline Match System (180度规则与视线匹配系统)

## 1. 180-Degree Rule (The Axis Rule)

In dialogue or chase scenes, there exists a virtual **action axis**. The camera must remain on the same side of this axis, otherwise character eyelines will be confused -- this is the 180-degree rule.

```
+-------------------------------------------------+
|             180-Degree Rule Diagram (Top View)    |
|                                                  |
|         [X] NG Zone (Crossed Axis)               |
|    ====================================  <- Action Axis
|         [O] OK Zone                              |
|                                                  |
|    [Char A] (looks right) <-- eyeline --> [Char B] (looks left) |
|                                                  |
|    CAM1 [O]         CAM2 [O]         CAM3 [O]   |
|    (OTS wide)       (OTS close-up)   (OTS close-up) |
|                                                  |
|                        CAM4 [X] (Crossed Axis!)   |
|                        Char A suddenly "looks left" |
|                        Audience spatial sense broken |
|                                                  |
|   Rules:                                          |
|   +-- Camera always on same side of axis          |
|   +-- Char A always looks right in frame          |
|   +-- Char B always looks left in frame           |
|   +-- Must cross axis: use neutral shot (front/back) as bridge |
+-------------------------------------------------+
```

### Axis Notation in Storyboard

```
Dialogue scene two-person axis notation:

+-----------------------+  +-----------------------+
| S2-001  MS  50mm      |  | S2-002  MCU  85mm     |
| AXIS: A<->B           |  | AXIS: SAME SIDE       |
| CAM: OTS A(right side)|  | CAM: OTS B(left side) |
|                       |  |                       |
|  [Char A](looks R)-> [Char B]  |  |  [Char A]    <-[Char B](looks L) |
|  [OTS over-shoulder]  |  |  [Reverse OTS]        |
|                       |  |                       |
|  Char A on frame right|  |  Char A on frame left |
|  Char A looks right   |  |  Char A STILL looks right! |
+-----------------------+  +-----------------------+
         [O]                        [O]
    (Same side, no cross)      (Same side, no cross)
```

### Legal Axis Crossing Methods

When the story requires crossing the axis (e.g., character emotional shift, perspective change), use these "legal" crossing methods:

| Method | Description | Example Shot |
|--------|-------------|--------------|
| Neutral Transition Shot | Insert front or back shot before crossing | Char A front CU (neutral) -> cut to other side of axis |
| Camera Movement Cross | Camera moves across axis within the shot | Steadicam moves from Char A left to right side |
| Character Action Cross | Character turns, creating a new action line | Char A turns around, establishes new action line |
| Insert Shot Cross | Insert prop/environment close-up before crossing | Insert clock close-up -> return to new angle |
| Time Jump Cross | Re-establish space after time ellipsis | "One hour later" -> new camera position |

### Marking Axis Crossing Intent in Storyboard

```
S2-005  CU  85mm  AXIS CROSS [WARNING]
-> Insert Char A front close-up (neutral transition), next shot crosses axis
-> S2-006 will shoot from the other side of the axis
```

## 2. Eyeline Match

Ensure character eyeline directions correctly align in shot/reverse-shot sequences:

```
+--------------------------------------------------+
|            Eyeline Match Rules                     |
+--------------------------------------------------+
|                                                  |
|  Char A (tall) looks down -> <- Char B (short) looks up |
|                                                  |
|  Correct notation example:                        |
|  +------------+       +------------+             |
|  | S3-004     |       | S3-005     |             |
|  | MCU Char A |       | MCU Char B |             |
|  | EYE LOOK v | --->  | EYE LOOK ^ |             |
|  | (looking down) | match | (looking up)  |             |
|  | LA low angle|       | HA high angle|            |
|  +------------+       +------------+             |
|                                                  |
|  Eyeline Notation Symbols:                        |
|  EYE LOOK->  Character looks right                |
|  EYE LOOK<-  Character looks left                 |
|  EYE LOOK^   Character looks up (looking up at something/someone) |
|  EYE LOOKv   Character looks down (looking down at something/someone) |
|  EYE LOOK NE  Character looks upper-right         |
|  EYE OFF-SCREEN  Looking off-screen               |
|  EYE DIRECT-TO-CAMERA  Looking at camera (breaking 4th wall) |
|                                                  |
|  Key Rules:                                       |
|  +-- In shot/reverse-shot, A's eyeline direction = opposite of B's |
|  +-- Eyeline height difference must match character height difference |
|  +-- Eyeline noted in lower-left of each storyboard panel |
|  +-- 3+ consecutive dialogue shots must include axis top-view diagram |
+--------------------------------------------------+
```