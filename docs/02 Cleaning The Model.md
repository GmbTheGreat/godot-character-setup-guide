# Cleaning the Character

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/70e9e431-8118-41d5-8548-7d15c8f75bd5" />

<br><br>

> **The character is here. Now let's clean it up.**
>
> Before we send the character to Mixamo, we want to make sure Blender contains only what we actually need.
>
> Think of this as preparing the character's backpack before the journey: remove the unnecessary stuff, keep the important parts, and make the next step easy.

<br>

## 🧹 What Are We Cleaning?

A downloaded character can contain much more than the visible character.

It may include:

- Extra objects
- Parent hierarchies
- Old armatures
- Root objects
- Modifiers
- Vertex groups
- Import-related objects

For this guide, our goal is simple:

**Keep the character mesh clean and remove the old rigging setup.**

Why?

Because **Mixamo will create a fresh rig for us** in the next chapter.

<br>

> [!TIP]
> **Don't worry if some of these Blender terms are new.**
>
> We will explain each one exactly when we use it. You don't need to memorize everything before starting.

<br>

## 🛠️ What Do We Need?
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/41928688-f1b2-42e0-b495-03ec12bc772f" />

<br>

You need a 3D application that can open and edit your character model.

There are many options available, but for this guide we'll use:

**Blender**

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/07004ee3-e25f-4b52-a97a-39bd55508612" />

<br>

It is free, powerful, and works very well for this workflow.

<br><br>

## 🎭 Start With Your Character

You may have:

- Created the character yourself.
- Downloaded it from an online 3D resource.
- Received it from another artist.

For our example, we'll use a character downloaded from **Sketchfab**.

**Reference model:**  
[The Reference Model](https://sketchfab.com/3d-models/modular-humanoid-characters-male-free-demo-dd4cb5e8d0e74cd9b05c44b0f738d2d9)

**Credit:** joaobaltieri

<br>

> [!NOTE]
> You don't have to use this exact character.
>
> The important part is understanding the cleanup process. You can follow the same steps with your own humanoid character.

<br>

# 1. 📥 Import the Character

Open Blender and create a new scene.

At the top-left:

**File → Import**

Blender supports several common 3D formats, such as:

- FBX
- GLB / GLTF
- OBJ
- And others

Our example character is a **GLB** file.

<img width="251" height="489" alt="image" src="https://github.com/user-attachments/assets/d7736997-56eb-4123-ba56-8d5740779d44" />

Select your character file and import it.

You should now see your character inside Blender.

<img width="1919" height="1006" alt="image" src="https://github.com/user-attachments/assets/368fc65d-d448-4e25-b16a-16d5a9ea196d" />

<br>

# 2. 🌳 Understand the Outliner

Look at the **top-right corner** of Blender.

This is the **Outliner**.

It shows the objects that exist inside your scene and how they are organized into hierarchies.

<img width="341" height="235" alt="image" src="https://github.com/user-attachments/assets/b5b6a010-092e-4d1a-bd65-cb498b4b710e" />

At first, the list may look a little confusing.

That's completely normal.

We are going to clean it step by step.

<br>

# 3. 🔓 Clear the Imported Parent Hierarchy

Our downloaded model is actually a whole character pack, so several objects are connected through parent relationships.

Select the objects you want to clean.

Press:

`A`

This selects everything in the current view.

Then:

**Right-click → Parent → Clear Parent and Keep Transformation**

<img width="342" height="532" alt="image" src="https://github.com/user-attachments/assets/ca4a22c7-fcb7-4958-8e32-6c70f4afea1f" />

<br>

<details>
<summary>💡 Why are we using "Clear Parent and Keep Transformation"?</summary>

A **parent** controls another object's transformation.

For example, one object can follow another object's:

- Location
- Rotation
- Scale

When we clear the parent, we remove that relationship.

But **Keep Transformation** makes sure the objects stay where they currently are.

So we are essentially saying:

> "Stop following the parent, but don't move."

This makes the imported hierarchy easier to clean.

</details>

After clearing the parent relationship, the objects should become individually visible in the Outliner.

Much easier to work with.

<br>

# 4. 🌱 Remove Unnecessary Root Objects

Now we can start removing the objects we don't need.

First, look through the Outliner for the **root objects**.

<img width="341" height="532" alt="image" src="https://github.com/user-attachments/assets/89f056ae-3ad0-49a9-ba34-3ab9d0f53ece" />

Select the unnecessary root objects and delete them.

Press:

`X → Delete`

<br>

> [!IMPORTANT]
> **Don't blindly delete everything.**
>
> We only want to remove objects that are part of the old/imported setup. Keep the actual character meshes.

<br>

<details>
<summary>💡 What is a "root" object?</summary>

A **root** is simply an object at the top of a hierarchy.

Think of it like a folder at the top of a folder tree.

It may not be part of the visible character itself. It can simply be used to organize or control other objects.

In Blender, the exact icon can vary depending on what kind of object was imported.

For this guide, the important idea is:

**We want to remove unnecessary hierarchy/control objects and keep the character mesh.**

</details>

<br>

# 5. 🦴 Remove the Old Armature

After removing the unnecessary roots, you should be left with the character mesh and an **armature**.

<img width="342" height="330" alt="image" src="https://github.com/user-attachments/assets/7e2f9570-46e0-4c3c-8171-df03f696e6fa" />

An **armature** is the skeleton used to control a character.

In Blender, it has a small stick-figure / bone-like icon in the Outliner.

We don't need this armature for our workflow.

**Select the armature → `X` → Delete**

<br>

<details>
<summary>💡 Why are we deleting the armature?</summary>

Because we want **Mixamo to create a fresh rig** for the character.

An existing armature may use:

- Different bone names
- A different bone hierarchy
- Different bone orientations
- Different animation expectations

Keeping it can make the later animation workflow more complicated.

Using a fresh Mixamo rig gives us a predictable starting point for the rest of this guide.

</details>

<br>

> [!NOTE]
> **Can I keep my existing armature?**
>
> Yes — custom rigs can absolutely be used in Godot.
>
> But that's a different workflow.
>
> This guide is intentionally using **Mixamo's rigging pipeline**, so we remove the old rig and start clean.

<br>


# 6. 👀 Check the Objects

After deleting the armature, take a look at the objects that remain.

<img width="824" height="783" alt="image" src="https://github.com/user-attachments/assets/35392224-d467-4190-b9a9-d86075b907e8" />

You should now mainly be looking at the character's actual mesh objects.

The Outliner should already look much cleaner.

<img width="338" height="289" alt="image" src="https://github.com/user-attachments/assets/c075836a-a648-4e56-ac5b-80018232a0ff" />

<br>

# 7. 🏷️ Give the Objects Proper Names

Now let's make the Outliner easier to understand.

Select the objects **one by one**.

Look at the character and identify what each object represents.

Then give it a useful name.

For example:

- `Body`
- `Head`
- `Shirt`
- `Pants`
- `Shoes`
- `Hair`

The exact names depend on your character.

<br>

> [!TIP]
> **Name things for humans, not machines.**
>
> `Object_001` tells you almost nothing.
>
> `Body` immediately tells you what you're looking at.

<br>

## 🎨 Make the Character Easier to See

Blender has several viewport shading modes.

For this step, use **Material Preview**.

It is the small viewport shading option near the upper-right side of the viewport.

<img width="258" height="28" alt="image" src="https://github.com/user-attachments/assets/afc37956-ba0e-43e0-8e44-a138a957a776" />

Material Preview lets you see the character with its materials instead of looking at a plain solid model.

That makes identifying clothing and body parts much easier.

After renaming the objects, your Outliner should look much cleaner.

<img width="340" height="284" alt="image" src="https://github.com/user-attachments/assets/1ab0e1b2-614b-4d6c-9e4a-0c883adad7c4" />

<br>

# 8. 🗑️ Remove `glTF_not_exported`

If your imported character contains a hierarchy named:

`glTF_not_exported`

we don't need it for this workflow.

Select the `glTF_not_exported` hierarchy and delete the whole hierarchy.

<br>

<details>
<summary>💡 What is `glTF_not_exported`?</summary>

This is an import/export-related hierarchy that can appear with glTF-based assets.

It is not part of the character's actual mesh.

Since we are preparing the character for a new Mixamo rig, we don't need to keep this imported organization.

<br>

</details>

<img width="341" height="298" alt="image" src="https://github.com/user-attachments/assets/ed0ed8e2-313a-4ba6-864b-8b790bc6bd98" />

Now the character should be reduced to the useful mesh objects and their data.

<br>

# 9. 🔧 Remove Old Modifiers

There is one more important cleanup step.

Select a character mesh.

On the right side, look through the Properties editor for the **Modifiers** tab.

The icon looks like a **blue wrench**.

You may also see vertex groups represented by a small list/box-style control in the mesh data.

<img width="342" height="988" alt="image" src="https://github.com/user-attachments/assets/3c5b6596-81c4-4942-99a5-f0bda1ad8899" />

<details>
<summary>💡 What are modifiers and vertex groups?</summary>

### Modifiers

A **modifier** changes or processes a mesh without permanently changing the original geometry.

For example, a modifier can be used for:

- Deformation
- Subdivision
- Mirroring
- Rigging

In our case, we may find an **Armature modifier** left over from the old rig.

We don't need that old rig anymore.

### Vertex Groups

A **vertex group** is a named collection of vertices.

Rigging systems use them to determine which parts of a mesh are influenced by particular bones.

For example:

> A group can tell Blender which vertices should move with an arm bone.

Because we're creating a fresh Mixamo rig, we don't want the old rig's deformation data hanging around.

</details>

<br>

# 10. 🦾 Remove the Armature Modifier

With the mesh selected, open the **Modifiers** tab.

Look for an **Armature** modifier.

<img width="343" height="307" alt="image" src="https://github.com/user-attachments/assets/212a8fd1-ddee-413d-b1bf-fcd3dc7f4b0f" />

Click the **X** on the modifier to remove it.

<img width="343" height="291" alt="image" src="https://github.com/user-attachments/assets/de3edebb-11fd-4d84-9041-32308d9735e4" />

Repeat this for the other character mesh objects if they also contain an old Armature modifier.

<br>

> [!WARNING]
> **This cleanup assumes you are starting a fresh Mixamo rig.**
>
> If you are trying to preserve a custom rig and its deformation setup, do **not** blindly remove modifiers.

<br>

# 11. 🧩 Remove Old Vertex Groups

Now let's remove the old vertex groups.

Select a mesh object.

Go to **Object Data Properties**.

The icon is a **green triangle**.

<img width="342" height="657" alt="image" src="https://github.com/user-attachments/assets/15fda4da-526c-430e-91db-8054a4ab5384" />

<br>

<details>
<summary>💡 What is Object Data Properties?</summary>

Object Data Properties contains information that belongs directly to the mesh itself.

For a mesh object, Blender represents this tab with a **green triangle icon**.

This is where we can access mesh-related data such as:

- Vertex groups
- Shape keys
- UV maps
- Other mesh data

For this cleanup, we are interested in the existing vertex groups.

<br>

</details>

Open the vertex group dropdown.

You should see a small dropdown control near the group list.

<img width="342" height="656" alt="image" src="https://github.com/user-attachments/assets/74a1afac-3193-46e6-bacb-a0af6f1f03da" />

Choose:

**Delete All Groups**
Repeat this for each character mesh object.

<img width="344" height="466" alt="image" src="https://github.com/user-attachments/assets/d3601dcd-219b-4c46-be3d-30f8a4747c0a" />

<br><br>

> [!IMPORTANT]
> We are removing the old vertex groups because this tutorial is rebuilding the character's rig from scratch with Mixamo.
>
> If your model contains important custom deformation data that you want to preserve, stop here and keep that data.

<br>

# ✨ We're Clean!

That's it.

Your character should now be:

- 🧍 Clean mesh
- 🧹 Free from unnecessary imported hierarchy
- 🦴 Free from the old armature
- 🔧 Free from the old Armature modifiers
- 🧩 Free from the old vertex groups
- 🏷️ Properly organized and named
- 🎨 Easy to inspect in Blender

<br><br>

<img width="344" height="466" alt="image" src="https://github.com/user-attachments/assets/d3601dcd-219b-4c46-be3d-30f8a4747c0a" />

<br><br>

> [!TIP]
> **Take a breath. You're done with Blender cleanup.**
>
> The character is now ready for the next stage:
>
> **Rigging with Mixamo.**

<br>

# 12. 📦 Export the Character for Mixamo

Our character is clean.

Now we need to send it to **Mixamo**.

Go to:

**File → Export → FBX (.fbx)**

Blender supports several export formats, but for this workflow, choose **FBX**.

<img width="251" height="489" alt="image" src="https://github.com/user-attachments/assets/d7736997-56eb-4123-ba56-8d5740779d44" />

<br><br>

<details>
<summary>💡 Why are we using FBX?</summary>

**FBX** is a widely used 3D interchange format, especially for **characters, skeletons, animations, and game engines**.

It is a good fit for this workflow because we are moving a character between different tools:

**Blender → Mixamo → Godot**

FBX is commonly supported across this type of pipeline and can carry the character mesh and, later, rigging and animation data.

But there is another important reason:

### 🎯 Mixamo's supported upload formats

When you upload a character to Mixamo, the upload options are limited compared with Blender's many export formats.

Mixamo mainly gives you only a small number of supported character formats, including **FBX**.

So instead of choosing a format that Blender supports but Mixamo doesn't, we use **FBX** as the safe and practical choice for this workflow.

In other words:

> **Blender gives us many doors. Mixamo only opens a few of them. FBX is one of the doors Mixamo expects us to use.**

</details>

<br>

> [!TIP]
> **Keep the original Blender file!**
>
> Exporting an FBX does not replace your `.blend` file.
>
> Keep the Blender project safely saved so you can come back and make changes later.

<br>

## 🚀 Ready for Mixamo

The character is now:

- 🧹 Cleaned
- 🏷️ Organized
- 🦴 Free from the old armature
- 🔧 Free from the old rigging setup
- 📦 Exported as FBX

**Next stop: Mixamo.**
