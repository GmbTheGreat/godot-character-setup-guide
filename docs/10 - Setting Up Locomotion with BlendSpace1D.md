# 🏃 Creating the Locomotion BlendSpace

Now we can combine our **State Machine** with a **BlendSpace1D**. Inside the State Machine, right-click on an empty area and select:

**BlendSpace1D**

Rename the new node to:

`Locomotion`

Then connect:

```text
Start → Locomotion
```

Our State Machine now looks like:

<br>

<img width="873" height="163" alt="image" src="https://github.com/user-attachments/assets/c4fff8b1-0b75-4e58-bf5e-400e6bcfffb2" />

<br><br>

Double-click **Locomotion** to open the BlendSpace1D. Here we will add our **Idle and Walk** animations and use movement speed to smoothly blend between them.

<br>

> [!TIP]
> The **State Machine** controls the character's major animation states, while **BlendSpace1D** handles the blending of our locomotion animations.

<br>

## Setting Up Locomotion with BlendSpace1D

After opening the **BlendSpace1D** node, you will see a graph with values ranging from **-1.0 to 1.0** by default. 
For our basic **Idle → Walk** setup, let's change this range.

<br>

<img width="1350" height="398" alt="image" src="https://github.com/user-attachments/assets/a7c08ca5-cbf2-4da1-b231-8661df259386" />

<br><br>

Set:

* **Left / Start:** `0.0`
* **Right / End:** `3.0`

This gives us a simple range for blending between Idle and Walk.

<br>

> [!TIP]
> You can also adjust the graph's visible range to **1** if you want to see the graph more broadly instead of focusing on a detailed section.

<br>

### Add Idle and Walk

Now right-click on an empty area of the BlendSpace and add:

* **Idle**
* **Walk**

Place the animations at:

<br>

<img width="1350" height="396" alt="image" src="https://github.com/user-attachments/assets/3bda1885-2bde-4ace-b5c9-b78f754488e4" />

<br><br>

Set:

* **Idle** → `0.0`
* **Walk** → `3.0`

Make sure **Snapping** is enabled. This makes it much easier to place the animation points precisely at the required values. 
Now our BlendSpace1D has the basic **Idle → Walk** locomotion setup ready.

<br>

## 🔗 Connect the Character Script

Now attach the **[Character Movement & Animation Script](#)** to the `CharacterBody3D` root node.

This script connects our character movement with the **Locomotion BlendSpace1D**, allowing the Idle and Walk animations to respond to movement.

> [!WARNING]
> If you are using the reference script, make sure your **BlendSpace1D state is named `Locomotion`**. The script uses this exact name to access the BlendSpace parameter.

After attaching the script, select the **CharacterBody3D** and look at the Inspector. 
Under the exported **Animation Tree** property, assign your:

`AnimationTree`

Now the script can communicate with the AnimationTree and control the BlendSpace. 
Now you can **Play the game and test the result**. 
Your character should no longer simply snap between animations. Instead, the **BlendSpace1D smoothly blends** between Idle and Walk based on the character's movement speed. 
Once this is working, you can use the **same process and script logic** to add more animations, such as **Run** and other locomotion animations.
