# Setting Up Character Animations
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/e44c0f2e-b2f9-497f-a77b-4cb0e9751694" />

<br><br>

We also have our animations ready — Idle, Walk, Run and the other animations we prepared earlier. But there is one problem. Right now, the character can move, but the animations are not automatically responding to what the character is doing.

We need a system that can answer questions like:

> Is the character standing still?
> 
> > Play Idle.

> Is the character moving slowly?
> 
> > Play Walk.

> Is the character moving quickly?
> 
> > Play Run.

This is where AnimationTree comes in.

<br>

## Understanding AnimationPlayer and AnimationTree

Before adding anything, let's understand the two systems we are going to use. We already have an `AnimationPlayer`. The `AnimationPlayer` is responsible for storing and playing animation data.

For example:

```
AnimationPlayer
├── Idle
├── Walk
├── Run
├── Jump
├── Fall
└── Land
```

But simply having all these animations does not automatically create a system that decides when to play each one.

That's where `AnimationTree` comes in.

<br>

<img width="185" height="69" alt="image" src="https://github.com/user-attachments/assets/b536a456-f4e0-47b8-993a-2bf713e47d15" />

<br><br>

<details>
<summary>💡 What is AnimationTree?</summary>

Think of AnimationPlayer as the place where our animations live, while AnimationTree is the system that controls how those animations are used together.

For example:

AnimationPlayer
      ↓
Contains our animations

AnimationTree
      ↓
Controls and blends those animations

This becomes especially useful when we want smooth transitions between animations.

Instead of suddenly switching:

Idle → Run

we can create a system where the character smoothly moves through the appropriate animation based on its movement.
</details>

<br>

> [!IMPORTANT]
> We are not replacing AnimationPlayer with AnimationTree. The AnimationPlayer still contains the animation data. AnimationTree uses that animation data to create more advanced animation behavior.

<br>

## Add an AnimationTree

Select the character node that contains your `AnimationPlayer`.

Then add:

> `AnimationTree`

Your animation-related hierarchy should now contain both:

```
AnimationPlayer
AnimationTree
```

<br>

<img width="285" height="355" alt="image" src="https://github.com/user-attachments/assets/cd55680f-6059-4d28-8ec6-05508ee9ca6d" />

<br><br>















## Setting Up the Animation Tree Root

<img width="278" height="308" alt="image" src="https://github.com/user-attachments/assets/bd184047-8caa-49dc-b107-2fc754df9fef" />

<br><br>

Our **AnimationTree** is now added to the character, but you may notice a warning telling us that the **Tree Root** has not been set yet.
 So, what exactly is a **Tree Root**?
 
 Think of it as the **main brain of our animation system**. It decides how our animations will be organized, blended, and switched.

Godot provides several types of animation root nodes, and the right choice depends on the kind of animation system your game needs. ([Godot Engine documentation][1])

<br>

## 🌳 Choosing a Tree Root

When you open the **Tree Root** option, you will see several choices.

### `AnimationNodeAnimation`

This is the simplest option.

It simply plays **one animation** from the AnimationPlayer.

This can be useful when you only need to play a single animation, but it is generally **not used as the main root** for a complete character animation system. ([Godot Engine documentation][1])

<details>
<summary>💡 Think of it like this</summary>

You are basically saying:

> "Just play this one animation."

There is no state switching or complex blending involved.

</details>

---

### `AnimationNodeBlendTree`

A **BlendTree** gives you a larger graph where you can combine different animation nodes.

It can contain things such as:

* Animation nodes
* Blend nodes
* One-shot animations
* Other animation systems
* Multiple layers of animation logic

This is useful when you want to build a more advanced animation graph with several systems working together. ([Godot Engine documentation][1])

<details>
<summary>💡 Think of it like this</summary>

Instead of choosing one animation, you are building an entire **animation workspace** where different animation systems can be connected together.

</details>

---

### `AnimationNodeBlendSpace1D`

A **BlendSpace1D** blends animations along **one axis**.

For example:

`Idle → Walk → Run`

You can control one value, such as **movement speed**, and Godot will blend between the animations based on that value. ([Godot Engine documentation][2])

This is extremely useful for **locomotion systems**.

We will use this later when we want our character to smoothly transition between:

* Idle
* Walk
* Run

---

### `AnimationNodeBlendSpace2D`

A **BlendSpace2D** works similarly, but instead of one value, it uses **two dimensions**.

This allows you to place animations in a 2D space and blend between them based on two values. ([Godot Engine documentation][2])

For example, you could create a directional locomotion system:

```text
        Forward
           ↑
           |
Left ←─────┼─────→ Right
           |
           ↓
        Backward
```

This can be useful when your character has separate animations for moving in different directions.

<details>
<summary>💡 When would we use BlendSpace2D?</summary>

Imagine a character who can move:

* Forward
* Backward
* Left
* Right
* Diagonally

A BlendSpace2D can help smoothly blend between those directional animations.

We don't need this complexity for our basic setup yet.

</details>

---

### `AnimationNodeStateMachine`

A **State Machine** organizes animations into different **states** and controls how the character moves from one state to another. ([Godot Engine documentation][1])

For example:

```text
Idle → Walk → Run
 ↓      ↓
Jump → Fall → Land
```

Each state can contain an animation or even another animation system.

This makes State Machines especially useful for character animation because a character naturally has different states.

<details>
<summary>💡 Why is State Machine the best starting point?</summary>

A humanoid character already behaves like a collection of states.

For example:

**Idle**
The character is standing.

**Walk**
The character is moving slowly.

**Run**
The character is moving quickly.

**Jump**
The character has started jumping.

**Fall**
The character is coming back down.

**Land**
The character has touched the ground again.

A State Machine gives us a clean way to organize these behaviours and define **when one animation should transition into another**.

</details>

---

## 🎯 Which One Should We Use?

There is **no single Tree Root that is correct for every game**.

The choice depends on the animation system you are building.

| Tree Root                   | Best suited for                             |
| --------------------------- | ------------------------------------------- |
| `AnimationNodeAnimation`    | Playing a simple animation                  |
| `AnimationNodeBlendTree`    | Building complex animation graphs           |
| `AnimationNodeBlendSpace1D` | Blending animations using one value         |
| `AnimationNodeBlendSpace2D` | Blending animations using two values        |
| `AnimationNodeStateMachine` | Organizing animation states and transitions |

For our guide, we are building a **basic humanoid character setup**, so we don't need to build everything at once.

We will introduce these systems **step by step** as our character becomes more advanced.

For now, the **State Machine** is the easiest starting point because it gives us a simple and clear foundation for understanding character animation states.

<br>

> [!TIP]
> **Don't try to build the entire animation system at once.**
> We will start with the basic State Machine, then introduce **BlendSpace1D**, **BlendSpace2D**, and other systems when we actually need them.

<br>

## 📚 Official Godot Documentation

If you want to explore the complete system, the official Godot documentation is the best reference:

[Using AnimationTree — Godot Official Documentation](https://docs.godotengine.org/en/stable/tutorials/animation/animation_tree.html?utm_source=chatgpt.com)

[AnimationRootNode — Godot Official Documentation](https://docs.godotengine.org/en/stable/classes/class_animationrootnode.html?utm_source=chatgpt.com)

[AnimationNode — Godot Official Documentation](https://docs.godotengine.org/en/stable/classes/class_animationnode.html?utm_source=chatgpt.com)

<br>

> [!NOTE]
> **AnimationTree does not contain the actual animations itself.** The animations remain in the `AnimationPlayer`, while the `AnimationTree` controls how those animations are played, blended, and transitioned. ([Godot Engine documentation][1])

<br>

[1]: https://docs.godotengine.org/en/stable/tutorials/animation/animation_tree.html?utm_source=chatgpt.com "Using AnimationTree — Godot Engine (stable) documentation in English"
[2]: https://docs.godotengine.org/en/latest/tutorials/animation/animation_tree.html?utm_source=chatgpt.com "Using AnimationTree — Godot Engine (latest) documentation in English"
