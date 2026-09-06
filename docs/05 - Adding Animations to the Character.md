# Adding Animations to the Character

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/11efae2b-66b8-462d-a12c-593a34dbeab0" />

<br><br>

> Our character is now rigged.
> Now let's give it some **animations** and bring it to life.

<br>

## 🧍 Choose Your Character

You can use your own rigged character here.

For this tutorial, I'm using **Mixamo's Y Bot** because it makes the animation setup easier to understand.

If you're following this guide for the first time, I recommend trying the Y Bot as well.

You can download it directly from Mixamo.

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/a770a618-66cc-4e1a-a47c-36ff86ed835e" />

Here we have our clean Y Bot with its rig visible in the **Outliner**.

<img width="340" height="429" alt="image" src="https://github.com/user-attachments/assets/7ea148a1-30ab-4be3-bc7a-696b8319f9ec" />

<br><br>

## 🎬 Prepare the Animation Workspace

Our character currently has one animation by default: the **T-Pose**.

Now we'll prepare Blender to add more animations.

At the bottom, you'll find the **Timeline**.

<img width="1585" height="87" alt="image" src="https://github.com/user-attachments/assets/5202ece1-5ada-41a2-9b18-a56835de9c6d" />

Drag the top border upward to make the animation area larger and easier to work with.

<br>

## 📋 Open the Dope Sheet

On the left side of the Timeline, click the editor type button.

<img width="226" height="27" alt="image" src="https://github.com/user-attachments/assets/c5c2f00a-4068-45f0-a807-b1f1cf0f16bb" />

A list of animation editors will appear.

<img width="787" height="264" alt="image" src="https://github.com/user-attachments/assets/445f5b6c-8561-4b49-9c75-74f6428bc63f" />

Select:

**Dope Sheet → Action Editor**

<img width="429" height="28" alt="image" src="https://github.com/user-attachments/assets/c32323a1-f93e-48ab-bf10-23b601cc3401" />

The Action Editor is where we'll manage the character's individual animation actions.

<img width="157" height="189" alt="image" src="https://github.com/user-attachments/assets/a695600b-9b9e-4cee-8696-81abb1c1119c" />

<img width="1581" height="347" alt="image" src="https://github.com/user-attachments/assets/224f4b8f-2aeb-4930-ae72-e9252d0ad5fb" />

Now we're ready to start adding animations.

<br>

## 🧩 Understand the Animation Setup

Before adding animations, let's understand what we're looking at.

In the **Action Editor**, you'll see two important selectors.

<img width="369" height="30" alt="image" src="https://github.com/user-attachments/assets/a47811d6-a672-4748-a64f-a4f3a0b679d6" />

The **left side** is used to choose the **Action / Animation**.

The **right side** is used to choose the **Armature** that the action is assigned to.

So, in simple terms:

**Animation → Armature**

We need to make sure we're working with the correct animation and the correct character armature.

<br><br>

## 🏷️ Rename the T-Pose

For now, our Mixamo animation is named:

`mixamo.com`

To make the setup easier to understand, rename it to:

`T Pose`

<img width="372" height="32" alt="image" src="https://github.com/user-attachments/assets/936d3801-480c-484c-80bb-f6d56e85cee2" />

This will make it much easier to identify later.

<br><br>

# 🎞️ Open Nonlinear Animation

Now let's move from the **Dope Sheet** to **Nonlinear Animation**.

Click the editor type button in the top-left corner of the Dope Sheet.

Then select:

**Nonlinear Animation**

<img width="1574" height="362" alt="image" src="https://github.com/user-attachments/assets/2b33ee25-68ea-4090-8b28-d35da21faeb5" />

This is the **NLA Editor**.

Here we can see the armature and the animations associated with it.

<img width="204" height="52" alt="image" src="https://github.com/user-attachments/assets/353a790c-4ba4-4391-b29e-97ad5a281403" />

<br>

Each animation has a **Push Down** button.

<br>

<details>
<summary>💡 What does "Push Down" actually do?</summary>

When an animation is currently active in the Action Editor, it is the animation you're currently working with.

**Push Down** moves that active action into an **NLA Track**.

This allows the action to be stored and managed as part of the character's animation setup.

Think of it like putting an animation onto a shelf:

**Action Editor → Push Down → NLA Track**

The animation is not deleted. It is simply moved into the NLA system so we can manage it there.

</details>

<br>

### What about our T-Pose?

We **will not push the T-Pose** into the NLA tracks.

The T-Pose is useful as the starting pose, but we don't need it as a gameplay animation in Godot.

So we'll leave it as it is and move on.

<br>

# 🎬 Get an Animation from Mixamo

Now let's get our first real animation.

Go back to **Mixamo** and choose an animation.

For this example, we'll download:

**Idle**

<img width="1914" height="945" alt="image" src="https://github.com/user-attachments/assets/53eaf08d-4762-40a3-8714-e970681f76cf" />

Before downloading, make sure the settings look like this:

- **Format:** FBX
- **Skin:** Without Skin
- **Frame Rate:** 30 FPS
- **Keyframe Reduction:** Enabled

<details>
<summary>💡 What do these download settings mean?</summary>

### 📦 Format — FBX

We're using **FBX** because it is the format we're already using throughout this Blender → Mixamo → Blender workflow.

### 🧍 Skin — Without Skin

We already have our character model and its skin.

We only need the **animation and armature data** from this download.

Choosing **Without Skin** prevents Mixamo from sending another copy of the character mesh with every animation.

This keeps the workflow cleaner.

### 🎞️ Frame Rate — 30 FPS

This sets the animation to **30 frames per second**.

We'll use 30 FPS consistently for this workflow.

### 🧹 Keyframe Reduction

This option reduces unnecessary keyframes where possible.

The goal is to keep the animation data cleaner and lighter while preserving the movement.

</details>

Download the animation.

<br><br>

# 📥 Import the Animation into Blender

Now return to Blender.

Import the FBX animation just like you imported the character earlier.

You should now see something like this:

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/7b27ade9-6bc7-4336-87ad-8f5c3cdba544" />

Don't worry if this looks a little confusing.

We now have **two armatures**.

### 🧍 Main Armature

This is our Y Bot's original armature.

It currently contains the:

`T Pose`

### 🎬 Animation Armature

This is the new armature that came with our Idle animation.

It contains the:

`Idle`

Our goal is simple:

> **Take the Idle animation from the temporary armature and assign it to our main armature.**

<br><br>

## 🔢 Why Is It Called `Armature.001`?

<img width="206" height="112" alt="image" src="https://github.com/user-attachments/assets/7721a27d-1831-433b-ae30-fb3cc70b10a1" />

Both armatures originally have the same name:

`Armature`

Blender cannot have two objects with the exact same name in the same scene.

So Blender automatically renames the second one:

`Armature.001`

This is completely normal.

Because we downloaded the animation **Without Skin**, the temporary armature may appear without the character mesh.

<img width="340" height="375" alt="image" src="https://github.com/user-attachments/assets/77e7aef0-bb9d-497a-97de-9da3d0931c1c" />

That's exactly what we want.

We only need its animation.

<br><br>

# 🔄 Assign the Animation to Our Main Armature

Now let's move the Idle animation to our Y Bot's armature.

Go back to the **Dope Sheet → Action Editor**.

<img width="1580" height="362" alt="image" src="https://github.com/user-attachments/assets/c97d199e-5908-4713-9db5-dd5a445163cc" />

You may see something similar to:

`Armature.001 | mixamo.com | Layer0`

This is the animation action that came from Mixamo.

First, rename the action to:

`Idle`

Then select your **main Y Bot armature** from the Outliner.

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/91e0f977-c452-44bf-a7e9-dada3f1093e8" />

Once the main armature is selected, it becomes the armature associated with the Action Editor.

Now select the `Idle` action. and select the available slot.

<img width="380" height="28" alt="image" src="https://github.com/user-attachments/assets/8471568f-e9d2-4ff5-bef8-1c6e4828a395" />

You should now see the Idle animation working with the **main Y Bot armature**.

<img width="1919" height="1033" alt="image" src="https://github.com/user-attachments/assets/baa4125d-e916-48b6-9d53-2754c4e86a8e" />

<br><br>

> [!TIP]
> The temporary armature gave us the animation.
>
> Our main armature is now using that animation.
>
> That's the important part.

<br><br>

# 📌 Push the Idle Animation to NLA

Now go back to:

**Nonlinear Animation**

<img width="1576" height="363" alt="image" src="https://github.com/user-attachments/assets/a6f0de31-d6d4-495a-9ada-db263bcaf332" />

You should now see the **Idle** action associated with the main armature.

Click:

**Push Down**

<img width="1575" height="361" alt="image" src="https://github.com/user-attachments/assets/84d89b39-b5d1-4468-a195-ac981fc7aa5a" />

Now the Idle animation has been added to the main armature's **NLA Track**.

<br><br>

# 🗑️ Remove the Temporary Armature

We no longer need `Armature.001`.

The Idle animation has already been assigned to our main armature and pushed into the NLA track.

So select:

`Armature.001`

and delete it.

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/28d869a7-965c-4b56-9285-032be8eaec1d" />

Now we're back to a clean setup with:

**One character → One armature → Idle animation**

<br>

> [!IMPORTANT]
> You don't need to push the temporary armature's animation into NLA.
>
> We only take the animation from the temporary armature, assign it to our **main armature**, push the action down there, and then remove the temporary armature.

<br><br>

# 🔁 Repeat for Walk and Run

That's the complete process.

Now repeat the same workflow for the other animations you need.

For example:

- **Idle**
- **Walk**
- **Run**

When downloading **Walk** and **Run** from Mixamo, make sure:

- **Format:** FBX
- **Skin:** Without Skin
- **Frame Rate:** 30 FPS
- **In Place:** Enabled

<img width="954" height="848" alt="image" src="https://github.com/user-attachments/assets/ffdc0426-f0c7-4725-8dd2-c3939346b13c" />

<br><br>

> [!NOTE]
> **In Place** keeps the character's movement centered instead of moving the character forward through the scene.
>
> This is useful for game locomotion because the game engine can control the character's actual movement while the animation provides the walking or running motion.

<br><br>

# 🎉 Our Character Can Move!

We have successfully added:

**Idle → Walk → Run**

to our character.

<img width="1581" height="358" alt="image" src="https://github.com/user-attachments/assets/df62e8e1-91c5-4724-92d9-1a41f44ff053" />

And if you check the Outliner, you can see the animation setup inside the armature:

**Animation → NLA Tracks → Idle / Walk / Run**

<img width="339" height="315" alt="image" src="https://github.com/user-attachments/assets/ccd0a941-2244-41c5-8f59-b611b5c2af63" />

<br><br>

> [!TIP]
> **That's it!**
>
> We now have one clean character, one main armature, and multiple animations ready for the next stage.

<br>

> Now we can export this in glb format with proper name `HeroCharacterModel.glb`
