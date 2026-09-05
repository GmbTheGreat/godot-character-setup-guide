# Rigging the Character with Mixamo
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/53d51d2b-3ab7-430a-8232-1b17686165dc" />

The character is clean and ready.

Now it's time to give it a **skeleton** and make it ready for animation.

Let's move to **Mixamo**.

## 🌐 Open Mixamo

Open any browser and go to:

[Mixamo](https://www.mixamo.com/#/)

You should see the Mixamo interface.

<img width="1897" height="943" alt="image" src="https://github.com/user-attachments/assets/45510cb2-68d7-41b8-bbca-71fb1afd3b91" />

Now that we're here, let's understand the interface before we start rigging.

---

## 🎬 A Quick Look Around

On the **left**, you'll find the **Animations** section.

This is where you can browse and preview different animations for your character.

<img width="935" height="897" alt="image" src="https://github.com/user-attachments/assets/b8eeb711-5508-451c-ac61-9ac1a6d7f1e0" />

On the **right**, you'll find different options for working with the character and animations.

<img width="325" height="846" alt="image" src="https://github.com/user-attachments/assets/9512b54c-c110-487e-bed9-5735d7025940" />

<br><br>

> [!NOTE]
> Don't worry about all these options yet.
>
> We'll use them step by step as we move through the rigging process.

<br>

## 🧍 Choose Your Character

You have two options here.

### Option 1 — Use Your Own Character

You can upload the **FBX** file we exported from Blender.

Click:

**Upload Character → Upload Selected File**

Then select the cleaned FBX file you exported earlier.

For example:

`file.fbx`

Mixamo will then prepare your character for the rigging process.

### Option 2 — Use Mixamo's Y Bot

You can also use the **Y Bot** provided by Mixamo.

It is already available in a **T-pose**, so you can use it for testing without uploading your own model.

<br><br>

> [!TIP]
> **Learning or testing?**
>
> If you're following this guide just to understand the workflow, Y Bot is a quick way to experiment.
>
> If you're preparing your own game character, upload the FBX we cleaned and exported in the previous chapter.

<br>

## 🚀 Let's Rig It

Our character is now inside Mixamo.

Next, we'll tell Mixamo where the important parts of the body are so it can build the skeleton correctly.

After you click **Next**, Mixamo will show your character with several body markers.

<img width="940" height="598" alt="image" src="https://github.com/user-attachments/assets/04248185-0497-4285-b05f-e8e43201f48e" />

Your job is simple:

**Place each marker on the correct part of the character.**

You don't need to do anything complicated here. Just make sure every marker is positioned correctly.

The markers you need are:

- **Chin** → Place it on the character's chin.
- **Wrists** → Place each marker on the correct wrist.
- **Elbows** → Place each marker on the correct elbow.
- **Knees** → Place each marker on the correct knee.
- **Groin** → Place it around the character's groin / hip center.

<br><br>

> [!IMPORTANT]
> **Marker placement matters.**
>
> Take a moment to make sure every marker is sitting on the correct body part.
>
> You don't need pixel-perfect precision, but avoid placing a marker too far away from its intended joint.

<br>

<details>
<summary>💡 Why do we need these markers?</summary>

Mixamo uses these markers to understand the character's body structure.

They help Mixamo identify important points such as:

**Head → Arms → Elbows → Wrists → Legs → Knees → Hips**

Once Mixamo understands these points, it can generate a skeleton that fits your character.

Think of it as giving Mixamo a few landmarks:

> **"Here is the chin, here are the wrists, here are the elbows, and here are the knees."**

Mixamo can then use those landmarks to figure out the rest of the rig.

</details>

<br>

> [!TIP]
> **Don't rush this step.**
>
> If a marker looks slightly misplaced, simply drag it to the correct position before continuing.

<br>

Once all the markers are correctly placed, click **Next**.

Mixamo will now process your character and create the rig.

This may take around **2 minutes**.

<img width="940" height="600" alt="image" src="https://github.com/user-attachments/assets/855cd441-6d82-40a0-a181-32c28195e315" />

<br>

Here we go! Our character now has an **armature rig**.

<br>

<img width="936" height="598" alt="image" src="https://github.com/user-attachments/assets/fa46ff65-d02a-40d2-a7b5-006f107cba03" />

<br>

Now select any animation and you'll see your character playing it.

<br>

<img width="1905" height="943" alt="image" src="https://github.com/user-attachments/assets/42ec59ac-3e76-4579-aa83-69d5a9660d30" />

<br>

## 📥 Download the Rigged Character

Click **Download**.

A popup will appear with the download options.

<br>

<img width="698" height="209" alt="image" src="https://github.com/user-attachments/assets/8c74a6ea-468c-4c6a-a6b9-4952d7a67350" />

<br>

Set:

- **Format:** Binary (.fbx)
- **Pose:** T-Pose

Leave the other options as they are, then click **Download**.

Your rigged character is now ready to bring into Blender.
