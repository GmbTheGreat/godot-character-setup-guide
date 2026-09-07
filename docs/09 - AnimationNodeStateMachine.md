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

And that's our first animation system!

Next, we'll create our first animation state and connect it to the character's Idle animation.
