# Creating Our First Animation State Machine
<img width="1882" height="809" alt="image" src="https://github.com/user-attachments/assets/0eca1a8c-391b-4015-b798-baab55cf51d6" />

<br><br>

Now we can start using the AnimationTree properly.

We will build our animation system one step at a time, starting with the most basic and important part: the State Machine. In the AnimationTree inspector, under Tree Root, select:

`AnimationNodeStateMachine`

This will create a new State Machine as the root of our AnimationTree.

<br>

<details> <summary>💡 Why are we starting with a State Machine?</summary>

A character can have many different animation states:

Idle
Walk
Run
Jump
Fall
Land

A State Machine lets us organize these animations into separate states and later define how and when the character moves from one state to another.

For example:

Idle → Walk → Run

and later:

Idle → Jump → Fall → Land → Idle

This gives us a clean foundation before we start adding more advanced systems such as BlendSpace1D and BlendSpace2D.

</details>

<br>

## 🎬 Open the State Machine

Once you select `AnimationNodeStateMachine`, you will see a new option to open or edit the State Machine. 
Open it. You should now see the State Machine graph inside the AnimationTree. At first, it will be mostly empty. That's completely fine — this is where we will start building our character's animation logic.

<br>

> [!NOTE]
> We are not adding Idle, Walk, Run, or other animations yet.
> First, we are creating the State Machine itself. We'll add the animations as individual states in the next step.

<br>

## 🎬 Adding the Idle Animation

Select the **AnimationTree** tab. 
You should see two nodes: **Start** and **End**.

<br>

<img width="1044" height="365" alt="image" src="https://github.com/user-attachments/assets/328a63cf-402f-4f74-9273-b8a1651287a9" />

<br><br>

Right-click on an empty area and select:

**Animation → Idle**

This adds our **Idle animation** to the State Machine. 
Now select the **Connect Nodes** option from the top-left of the AnimationTree tab.

<br>

<img width="378" height="55" alt="image" src="https://github.com/user-attachments/assets/d0b80d3c-75a1-49ad-b3d2-650c55b15452" />

<br><br>

Drag from **Start** to **Idle**.

```text
Start → Idle
```

Done! Our character should now start playing the **Idle animation**.

<br>

> [!WARNING]
> **Can't see the Animation option when you right-click?**
> You most likely missed the **Anim Player** setup from the previous step. Select `AnimationTree` and make sure its **Anim Player** property is assigned to the `AnimationPlayer` inside `HeroCharacterModel`.
>
> Without this connection, the AnimationTree cannot read the animations from your character.

<br>

## 🚶 Adding the Walk Animation

Now we'll do the same thing and add the **Walk** animation.

Add:

**Animation → Walk**

Then connect **Idle → Walk**.

Done! But there is one small problem: Godot still doesn't know **when** it should play Walk. 
Idle plays by default because it is connected to **Start**, and the **Start connection acts as the initial command**.

<br>

### Set the Walk Transition

Click the transition arrow between **Idle** and **Walk**.

<br>

<img width="278" height="622" alt="image" src="https://github.com/user-attachments/assets/6f1d790d-67aa-4ceb-981a-1c61ab8e6dc2" />

<br><br>

In the Inspector, find **Advance → Expression** and enter:

`velocity.length() > 0.0`

Now the character will switch from **Idle → Walk** when the character starts moving. 
We also need to tell Godot when to return to Idle. 

Create another transition from **Walk → Idle** and set its Expression to:

`velocity.length() == 0.0`

Now our basic flow looks like:

<br>

<img width="923" height="223" alt="image" src="https://github.com/user-attachments/assets/3323fd4a-a0b2-4ad1-a528-132353b5cb67" />

<br><br>

> [!NOTE]
> These **Advance Expressions use GDScript expressions**. If you are using another scripting language or a different character-control setup, you can achieve the same transitions through your own script/code instead of using these expressions directly in the AnimationTree.
