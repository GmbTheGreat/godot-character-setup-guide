# Setting Up the Rigged Character

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/4f1b642d-db80-4a3e-845b-fd4096d7e731" />

<br><br>

> Our character is now rigged.
> Let's bring it back into **Blender** and prepare it for the next step.

<br>

## 🎨 Bring Back the Character's Texture

After importing the rigged character, you may notice that it looks like this:

<br>

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/7cc687d4-0b52-46e9-b83c-bc1652e022a9" />

<br>

This happens because Mixamo does not bring back your original texture images and complete material setup.

That's why we saved the texture files earlier in **02 - Cleaning the Character**.

Simply connect your character's texture image back to the **Principled BSDF** node.

<br>

<img width="1611" height="493" alt="image" src="https://github.com/user-attachments/assets/e1c89003-370d-4584-aa9f-080be84854b1" />

<br>

Once the image texture is connected, your character should look like the original again.

<br>

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/b6288b5e-8d24-443f-acd6-594eeafe50a7" />

<br><br>

> [!TIP]
> The material itself is usually still there — you may simply need to reconnect the missing texture image.

<br>

## 🦴 Understand the Armature

Look at the **Outliner** in the top-right.

You will see the **Armature** with a small dropdown arrow.

Click it to expand the hierarchy.

<br>

<img width="342" height="414" alt="image" src="https://github.com/user-attachments/assets/b6843428-a63c-4041-bcb8-516dac82f146" />

<br>

Now you can see the objects organized under the armature.

<br>

<details>
<summary>💡 What are the Armature, Animation, and Pose?</summary>

**Armature** is the character's skeleton.

It contains the bones and their hierarchy that control the character.

**Animation** is movement data that tells those bones how to move over time.

**Pose** is the current position of the character's bones.

In **Pose Mode**, you can select and move individual bones to create or adjust a character's pose.

Think of it simply:

**Armature = Skeleton**  
**Pose = Current position of the skeleton**  
**Animation = A sequence of poses over time**

</details>

<br>

## 🎬 Time to Add Animations

Now we can start adding animations to our rigged character.

<br>

> [!NOTE]
> For this part of the guide, I'm using **Mixamo's Y Bot** to make the structure easier to understand.
>
> You can continue with your own character — **you don't need to switch to Y Bot**.
