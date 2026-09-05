# Getting a Character Model
<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/ca3e7399-af43-4308-bcff-f6f6ce892efe" />


*Everything starts here*.

<br>

You want to add a character to your game, and now you need a **character model**.

Your model can come from anywhere:

- Made by you or your team.
- Downloaded from an online resource such as Sketchfab.
- Created using another 3D tool or service.

<br>

> [!TIP]
> You don't need to be a 3D character artist to follow this guide. You can start with a character model from an online resource and prepare it from there.

<br><br>

## What Happens Next?
<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/98666de1-d137-49b6-8d07-1eef1bc36cbe" />

*Getting the model is only the beginning*.

A downloaded or newly created character can contain extra objects, modifiers, messy hierarchy, or other things that we don't need.

Before we move forward, we'll **clean and prepare the character** so it is ready for the next steps.

Think of it like preparing our character before sending them on their journey.

<details>
<summary>💡 Why do we need to clean the character?</summary>

A character model downloaded from the internet is not always ready to be used directly in a game.

It may contain things we don't need, such as:

- Extra objects
- Unused modifiers
- Unnecessary materials
- Messy object or bone hierarchy
- Incorrect transforms or scale
- Other data that can cause problems later

Cleaning the character now gives us a **simple and predictable starting point** for rigging, animation, and eventually bringing the character into Godot.

You don't need to understand everything here yet. We'll go through each part step by step.

</details>

<br><br>

## 🦴 What Is a Rig?
<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/6c4efdb6-041c-4acb-a702-1ffd3c056016" />

*Before our character can walk, run, jump, or even wave at us, we need to give them a **rig***.

A rig is basically a skeleton made of bones that sits inside the character.

We can move and rotate these bones, and the character follows them.

<br>

> [!NOTE]
> **Model = Body**  
> **Rig = Skeleton**  
> **Animation = Movement**

You can create a rig yourself, or use a third-party tool to make one for you.

Some popular options are:

- Mixamo
- AccuRIG
- Auto-Rig Pro

For this guide, we'll use **Mixamo**.

<br><br>

## What Is Mixamo?
<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/8aad2dd6-147b-41da-937d-3206fc97fc45" />

**Mixamo** is a service from Adobe that makes character rigging and animation much easier.

You can upload your character, let Mixamo create a rig for it, and then choose from a large library of ready-made animations.

This means we don't have to create every animation from scratch.

<br>

> [!TIP]
> Mixamo is especially useful when you're getting started with character animation or simply want to speed up your workflow.

<br><br>

## 🧹 Before We Go to Mixamo
<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/f6a41922-c4fb-4447-a951-7c2e1e285ad6" />

We know where we're going next: **Mixamo**.

But first, let's make sure our character is clean and ready.

In the next step, we'll prepare the model and remove anything that could cause problems later.

**Let's clean our character.**

<br><br>
