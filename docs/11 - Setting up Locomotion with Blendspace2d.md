## 🎯 Understanding BlendSpace2D

We have already used **BlendSpace1D** for our basic locomotion system. But Godot also provides **BlendSpace2D**, which is useful when we need to blend animations based on **two values**.

Instead of having a single line like BlendSpace1D:

```text
Idle ───────── Walk ───────── Run
 0              3              6
```

BlendSpace2D gives us a **2D space** where animation points can be placed in different directions.

### 🧭 How Does BlendSpace2D Work?

A BlendSpace2D has two axes:

* **X-axis** → left ↔ right
* **Y-axis** → backward ↔ forward

For example:

```text
                  Forward
                     ↑
                     |
             Forward-Left
                     |
Left ←──────────── Idle ────────────→ Right
                     |
             Backward-Right
                     |
                     ↓
                 Backward
```

Each animation is placed at a specific position in this space.

For example:

```text
Idle      = (0, 0)
Forward   = (0, 1)
Backward  = (0, -1)
Left      = (-1, 0)
Right     = (1, 0)
```

If you also have diagonal animations, they can be placed between these directions.

### 💡 Why Do We Need Two Dimensions?

With BlendSpace1D, we control the animation using **one value**, such as movement speed.

With BlendSpace2D, we can provide **two values at the same time**.

For example:

```text
X = movement left/right
Y = movement forward/backward
```

So if the character is moving diagonally forward-right, the BlendSpace2D receives values representing both directions and can blend the appropriate animations.

Instead of manually switching:

```text
Forward → Right
```

the BlendSpace can smoothly blend the two animations to produce a more natural **forward-right movement**.

### 🎮 Where Is It Commonly Used?

BlendSpace2D is particularly useful for characters that can move independently of where they are facing.

For example, an aiming or combat character might remain facing the target while moving:

```text
             Aim Direction
                   ↑
                   🧍
              ↙    ↓    ↘
           Move  Move   Move
           Left Forward Right
```

The character can therefore:

* Move forward while aiming forward.
* Move backward while continuing to face forward.
* Strafe left while facing forward.
* Strafe right while facing forward.
* Move diagonally while maintaining the same facing direction.

With the appropriate animations, BlendSpace2D can smoothly blend between these movements.

### 🔄 BlendSpace2D Is Not Just "A Better BlendSpace1D"

They solve different problems.

**BlendSpace1D:**

```text
Speed
 ↓
Idle → Walk → Run
```

Best when one value controls the animation, such as **movement speed**.

**BlendSpace2D:**

```text
Movement Direction
       ↓
Forward / Back / Left / Right
       ↓
Directional blending
```

Best when **two values** are needed to describe the animation, commonly movement direction.

> [!NOTE]
> BlendSpace2D does not automatically make a character strafe or move directionally. You still need the appropriate **movement logic and animations**. The BlendSpace simply provides the system for smoothly blending those animations based on the values your game sends to it.

### 🧩 How It Fits Into a Character Controller

BlendSpace2D can also be used inside a State Machine, just like our current BlendSpace1D.

For example:

```text
AnimationTree
└── State Machine
     ├── Idle
     ├── Locomotion
     │    └── BlendSpace2D
     │         ├── Forward
     │         ├── Backward
     │         ├── Left
     │         └── Right
     ├── Jump
     └── Fall
```

So remember the relationship:

> **State Machine** decides *which major state the character is in*.
> **BlendSpace1D/2D** decides *how animations are blended inside that state*.

For our current character, we are using **BlendSpace1D** because the character turns toward its movement direction. If we later introduce **aiming, combat, or strafing**, BlendSpace2D becomes a much more useful option.
