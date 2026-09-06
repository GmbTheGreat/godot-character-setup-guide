# Bringing the Character into Godot

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/834cd774-1405-42d3-a789-e5ec50273602" />

<br><br>

Our character is now rigged and has its animations ready.

Now let's bring everything into **Godot** and start setting up our character for the game.

<br><br>

## 🎮 Create or Open Your Project

You can use an existing Godot project or create a new one if you're following this guide for learning.

For this tutorial, I'm creating a new project called:

`Character Pipeline`

<img width="562" height="535" alt="image" src="https://github.com/user-attachments/assets/c16f3a37-1a12-429e-820a-609aa5d013ac" />

Once the project opens, you'll see the Godot editor.

This main area is the **Viewport**.

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/529a54d5-4a19-4df9-8ba9-981d97e02198" />

---

## 📦 Add the Character to the Project

Now let's add our:

`HeroCharacterModel.glb`

Look at the **FileSystem** panel in the bottom-left corner.

<img width="284" height="478" alt="image" src="https://github.com/user-attachments/assets/48a78357-369c-4926-9ca1-884445a7f37d" />

Right-click the `res://` folder.

Select:

**Open in File Manager**

<img width="538" height="476" alt="image" src="https://github.com/user-attachments/assets/3ac88a50-a8de-45aa-8549-76638e55f119" />

This will open your Godot project's folder.

Now copy your:

`HeroCharacterModel.glb`

from the folder where you exported it and paste it into your Godot project folder.

<br>

> [!NOTE]
> `res://` represents the **root folder of your Godot project**.
>
> Files placed inside this folder become part of your Godot project and appear in the FileSystem panel.

<br>

Once the file is copied, Godot will automatically detect and import it.

You should now see your character model inside the **FileSystem** panel.

<img width="288" height="333" alt="image" src="https://github.com/user-attachments/assets/6f2eaf6f-7e0a-44ff-9fc4-fd7613fdfbd1" />

<br><br>

> [!TIP]
> **That's it!**
>
> Our character is now inside the Godot project.
>
> In the next step, we'll bring the model into the scene and start building the actual character setup.

<br>

## ⚙️ Open Advanced Import Settings

Double-click your `.glb` file to open **Advanced Import Settings**.

<img width="1534" height="888" alt="image" src="https://github.com/user-attachments/assets/ba00c0ce-fde4-4908-b30a-ba0520ff16f9" />

The layout may look familiar if you've worked with Blender.

Godot is simply showing the imported model and its data using its own editor and icons.

---

## 🎬 Configure the Animations

Open the **Animation** section and select any animation from the list.

<img width="1532" height="887" alt="image" src="https://github.com/user-attachments/assets/26e83ee2-5d14-4c18-87cb-509fa4b00ac9" />

On the right, you'll find the animation settings.

For our animations, make sure **Loop Mode** is set correctly.

<details>
<summary>💡 What is Loop Mode?</summary>

**Loop Mode** controls what happens when an animation reaches its final frame.

### None

The animation plays once and then stops.

This is useful for animations such as:

- Jump
- Attack
- Death
- Other one-time actions

### Linear

The animation continuously repeats from the beginning after reaching the end.

For our character's **Idle, Walk, and Run** animations, we want them to keep playing while the character remains in that state.

So we'll use:

**Idle → Linear**  
**Walk → Linear**  
**Run → Linear**

This allows the animation to continue smoothly instead of stopping after one playback.

</details>

<br><br>

## 💾 Save Each Animation to File

For every animation, enable:

**Save to File**

<details>
<summary>💡 Why do we need "Save to File"?</summary>

By default, animations can remain embedded inside the imported model resource.

**Save to File** separates the animation into its own file.

This makes the animations easier to:

- Manage
- Reuse
- Edit
- Reference later in our character setup

We'll be working with these animations later, so keeping them as separate resources makes our project easier to organize.

</details>

Make sure you enable **Save to File** for each animation you want to use.

<br><br>

## 🔄 Reimport the Character

Once the animation settings are ready, click:

**Reimport**

Godot will now reimport the character with the updated animation settings.

<br>

> [!TIP]
> **Take a quick look at your animations after reimporting.**
>
> If everything looks correct, we're ready to move on to setting up the character inside the scene.

<br><br>

## 🧩 Create an Inherited Scene

Right-click on `HeroCharacterModel` in the **FileSystem** panel.

Select:

**New Inherited Scene**

<img width="623" height="527" alt="image" src="https://github.com/user-attachments/assets/4ac59ab7-a7f4-4293-9175-5116e67dd189" />

Godot will open a new inherited scene with our imported character.

You should now see the character with a clean node structure on the left.

<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/7f9bc63d-9bcb-4ddb-8b32-9dfb496962f0" />

You can also see that an **AnimationPlayer** node is already included.

<br>

> [!NOTE]
> If your imported character doesn't have an **AnimationPlayer**, don't worry.
>
> You can simply add an AnimationPlayer node yourself.

<br><br>

## 🎞️ Check the Animations

Select the **AnimationPlayer** node.

The **Animation** panel will appear at the bottom.

<img width="1352" height="286" alt="image" src="https://github.com/user-attachments/assets/fa254a71-9361-41a2-b976-d7bb5ddf216a" />

<br>

Here you'll find the animations we imported earlier.

Simply select **Idle** to preview it.

You can also open the **Animation** menu on the left and choose:

**Manage Animations**

From there, you can manage, rename, or delete animations.

<br>

> [!TIP]
> We won't change anything here yet.
>
> We'll come back to animation management when we start building the character's animation system.
