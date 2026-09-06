# Setting Up the Character

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/a31711e2-563e-45fb-8ad1-1cbc12f4b616" />

<br><br>

Our character is now inside Godot with its animations ready.

Now let's give it the **basic character structure** it needs to work properly in our game.

Open **New Scene** and create a root node as `CharacterBody3D`.

It actually depends on the type of object you are creating. You can choose between different physics body nodes such as `CharacterBody3D` or `RigidBody3D`, but for our humanoid character we will use `CharacterBody3D`.

<br>

<details>
<summary>💡 CharacterBody3D vs RigidBody3D — Which one should we use?</summary>

Both `CharacterBody3D` and `RigidBody3D` are physics body nodes, but they are designed for different purposes.

A `CharacterBody3D` is intended for characters that are **controlled by gameplay code**. This is what we want for our player because our character's movement, direction, gravity, and other behavior will be controlled by our character controller.

A `RigidBody3D`, on the other hand, is mainly intended for objects that should be **controlled by the physics simulation**. For example, a box that should fall, be pushed, roll around, or react naturally to physical forces can be a good candidate for a `RigidBody3D`.

Think of it this way:

```text
CharacterBody3D
        ↓
Gameplay code controls the character
        ↓
Player / NPC
```

while:

```text
RigidBody3D
        ↓
Physics simulation controls the object
        ↓
Physics-driven object
```

For our humanoid player, we want direct control over the character, so `CharacterBody3D` is the appropriate choice.

[!IMPORTANT]
> `CharacterBody3D` and `RigidBody3D` are not simply two versions of the same node. Choose the body type based on **who should control the object's movement** — your gameplay code or the physics simulation.

</details>

<br>

<img width="285" height="266" alt="image" src="https://github.com/user-attachments/assets/e6fcc993-ae91-4486-8bdd-1a3dea3edf60" />

<br>

Great! Now you have created a root node as a `CharacterBody3D`.

You may notice that the new character body has a small warning about collision. Let's take care of that now.

A character needs a collision shape so Godot's physics system can understand the physical space occupied by the character and how it interacts with other objects in the world.

Add a child node to the `CharacterBody3D`.

You can either press:

```text
Ctrl + A
```

or simply select the root node, right-click it, and choose **Add Child Node**.

Search for and choose:

```text
CollisionShape3D
```

<br>

<img width="284" height="241" alt="image" src="https://github.com/user-attachments/assets/b7a869c5-3999-48b6-b541-735c6688a114" />

<br>

Alright! Now the `CollisionShape3D` itself has another warning because we haven't assigned an actual collision shape to it yet.

On the right side of the Godot editor, you will see the **Inspector**. By default, this is where you can view and edit the properties of the selected node.

<br>

<img width="288" height="579" alt="image" src="https://github.com/user-attachments/assets/e2c7fca0-c203-48df-ab2a-eeb53c99903d" />

<br>

Find the **Shape** property in the Inspector.

Click it and select:

**CapsuleShape3D**

<br>

<details>
<summary>💡 Why are we using a CapsuleShape3D?</summary>

A humanoid character is generally tall and rounded around the top and bottom, which makes a capsule a very practical approximation of the character's body for collision.

We don't need the collision shape to perfectly match every part of the character's visible mesh.

Our character model may contain detailed geometry such as:

```text
Head
Hair
Arms
Fingers
Torso
Legs
Shoes
Clothing
```

The physics system does not need to calculate collision around every single one of those details for a normal player character.

Instead, we can use a much simpler shape that represents the character's main physical body.

A capsule gives us:

- A simple collision shape.
- Smooth rounded ends.
- Predictable movement around the environment.
- Less unnecessary collision complexity.

So the idea is:

```text
Character Model
        ↓
Detailed visual appearance


CapsuleShape3D
        ↓
Simple physical representation
```

This separation is useful because the **visual model** is responsible for looking like the character, while the **collision shape** is responsible for representing where the character physically exists.

[!TIP]
> The capsule does not need to perfectly match the character mesh. Adjust its size so it roughly covers the character's body while keeping the shape simple and stable.

</details>

<br>

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/6ae8e3f8-f978-47e9-9d91-61a0ea2745ed" />

<br>

And you will see that the collision has now been added to our character.

<br>

Now let's add our character model to the scene.

You can either drag and drop the model into the scene as a child of the root node, or use **Instantiate Child Scene** to add an existing scene.

Since our character is a `.glb` file, we can simply drag it from the **FileSystem** dock and drop it into the scene.

<br>

<img width="1919" height="1026" alt="image" src="https://github.com/user-attachments/assets/4a2fe94b-48ae-4020-a68e-ca87ad592328" />

<br>

Once the character is added, adjust the **CollisionShape3D** we created earlier so that the capsule properly fits the character's body.

The collision shape does not need to match the model perfectly. Just make sure it covers the main body area and is positioned correctly around the character.

And that's it — our character model is now inside our player scene.

<br>

---

<br>

# Adding the Camera

Now that our character is in the scene, we need a camera so we can actually see the world from the player's perspective.

For our character, we are going to use a simple third-person camera structure.

Instead of adding a `Camera3D` directly under the `Player`, we will first create a `Node3D` that will act as our camera pivot.

Select the `Player` root node and add a:

```text
Node3D
```

Rename it to:

```text
CameraPivot
```

Then add a `SpringArm3D` as a child of `CameraPivot`.

Finally, add a `Camera3D` as a child of the `SpringArm3D`.

Our hierarchy should now look like this:

<br>

<img width="285" height="317" alt="image" src="https://github.com/user-attachments/assets/eebb9759-50b1-4d27-ad9a-68046bbcc194" />

<br><br>

<details>
<summary>💡 Why don't we just add a Camera3D directly to the Player?</summary>

We absolutely could add a `Camera3D` directly to the player, and for a very simple camera that can work.

But for a third-person character, we want a little more control over how the camera behaves.

That's why we separate the camera into three parts:

```text
CameraPivot
    ↓
SpringArm3D
    ↓
Camera3D
```

Each node has a different job.

The `CameraPivot` gives us a dedicated point around which the camera can rotate. This is especially useful when we want the player to look around without immediately rotating the entire character.

The `SpringArm3D` controls how far the camera sits behind the player and also helps prevent the camera from moving through nearby objects. If a wall gets between the player and the camera, the SpringArm can shorten its length and bring the camera closer to the player.

Finally, the `Camera3D` is the actual camera that renders the game view.

So instead of asking one node to handle everything, we have:

```text
CameraPivot
→ "Where should the camera rotate from?"

SpringArm3D
→ "How far away can the camera be?"

Camera3D
→ "What does the player actually see?"
```

This structure may look like a little more work now, but it gives us a much cleaner foundation for a third-person character.

Later, when we add camera rotation and player controls, we can control the pivot without having to rebuild the whole camera system.

[!TIP]
> A good character setup is not only about making something work right now. It is also about creating a structure that will be easy to control and extend later.

</details>

<br>

---

<br>

## Setting the Spring Arm Length

Now select the `SpringArm3D` node.

In the **Inspector**, find the **Spring Length** property and set it to:

```text
3.0
```

<br>

<img width="286" height="223" alt="image" src="https://github.com/user-attachments/assets/96af8e96-6db9-408e-84e0-65374a1f7ac2" />

<br>

This controls the distance between the `CameraPivot` and the camera when there is no obstruction.

With a value of `3.0`, our camera will sit relatively close to the character.

<br>

> [!NOTE]
> The exact camera distance is a design choice. We are using `3.0` here because it matches the setup used in this character pipeline. You can change it later if your character or desired camera style requires a different distance.

<br>

---

<br>

## Positioning the Camera Pivot

Now select the `CameraPivot` node.

In the **Transform** section of the Inspector, set:

```text
Position Y: 2.0
Rotation Y: 180.0
```

<br>

<img width="286" height="434" alt="image" src="https://github.com/user-attachments/assets/cf7bb11f-0966-435b-982f-6b46904dc247" />

<br><br>

The `Y` position raises the pivot above the player so that the camera is positioned around the character's upper body rather than around the feet.

The `Y` rotation changes the direction in which the SpringArm extends, which determines where the camera sits relative to the character.

The exact values can be adjusted depending on your character and the orientation of your imported model, but for our current setup use the values shown above.

<br>

---

<br>

## Camera Setup Complete

And there we go!

Our character now has a proper third-person camera structure.

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/96abbeab-20d5-44dd-a9b8-ce8b6be8ef51" />

Our scene should now look approximately like:

```text
Player
├── CharacterModel
├── CollisionShape3D
└── CameraPivot
    └── SpringArm3D
        └── Camera3D
```

The character model gives us the visuals, the collision shape gives the player a physical body, and the camera hierarchy gives us a clean foundation for our third-person view.

<br><br>

## Adding the Camera Pivot Script

Now that our camera hierarchy is ready, let's give our `CameraPivot` the script that will control its camera behavior.

Select the `CameraPivot` node and attach a new script to it.

Name the script:

```
camera_pivot.gd
````

Here is the script we will use:

**[Camera Pivot Script](#)**

<br>

> [!NOTE]
> The script is attached to the **`CameraPivot`** node because this node is responsible for controlling the camera's rotation and movement. The `SpringArm3D` and `Camera3D` remain as children and follow the pivot automatically.

<br>

---

## Testing the Camera

Now let's test what we have built so far.

<br>

> [!IMPORTANT]
> To test the character and camera properly, make sure you create a **separate game scene**. Our `Player.tscn` is the character scene, while the game scene is the actual world where we place and test our player.

<br>

Create a new game scene and then drag our:

```text
Player.tscn
```

into the scene.

Once the `Player` has been added to the game scene, set this scene as the **Main Scene** of the project.

Now press **Play**.

You should see your character from the third-person camera, and the camera should smoothly follow and move around the character.

<br>

<img width="1160" height="724" alt="image" src="https://github.com/user-attachments/assets/b72782da-24d9-42b2-bca0-d168655a2730" />

<br><br>

> [!TIP]
> If the camera doesn't behave as expected, first check that the `camera_pivot.gd` script is attached to the correct `CameraPivot` node and that your camera hierarchy is still:
>
> ```text
> CameraPivot
> └── SpringArm3D
>     └── Camera3D
> ```
>
> Also make sure the `Camera3D` is active in the scene.
























<br>

Now let's add some movement mechanics to our character through a script.

Select the CharacterBody3D node, which is the root node of our Player scene, and attach a new script to it.

<br>

<img width="485" height="496" alt="image" src="https://github.com/user-attachments/assets/4e5794f1-1c78-4a87-9993-08be07a3631a" />

<br><br>

When you create the script, Godot will provide you with a basic CharacterBody3D script template by default. For now, you can simply use this default template.

Click Create, and the basic movement mechanics will be added to our character. Now you can go back to your game scene and press Play to test the character.

You should be able to move the character around the scene.

<br>

> [!IMPORTANT]
> Before testing, make sure that in the movement code inside the if direction: section, you add a minus sign (-) before direction.z and direction.x when multiplying them by speed.
> 
> Otherwise, the movement direction will be reversed.
> 
> For example, the movement should use:
> 
> velocity.z = -direction.z * speed
> 
> velocity.x = -direction.x * speed

<br>

> [!NOTE]
> The default CharacterBody3D template uses Godot's default input actions, which are already available for basic testing. These include the arrow keys for movement and Space for jumping.
> 
> This is useful for testing our character quickly without creating an input system from scratch.
> 
> If you want to use your own controls, you can create custom input actions from:
> 
> Project → Project Settings → Input Map
> 
> Add your own input action names there, then replace the corresponding input names in the character script.
> 
> And that's it! Our character now has basic movement mechanics and can be tested inside the game scene.
