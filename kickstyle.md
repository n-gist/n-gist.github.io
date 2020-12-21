---
title: "KickStyle"
---

# KickStyle - Unity mobile game prototype

The plot of the game will contain career advancement of performances in different locations, with achievements, challenges and players rankings. Players will be able to open different styles of clothes and balls that will change playing style or give bonuses to the number of points earned.

<div class="videoWrapper">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/_D0q7-4XI_4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<br/>

During the game session, players will be able to move around the site for the pickup of auxiliary items, perform combo kicks and tricks at will or demand, and will also have special abilities, such as time dilation, excitement and fatigue relief and others.

The game will also have separate functionality for those who want to learn how to play with ball in real life. There you can watch description and execution of tricks in slow motion, with pause/rewind from any point of view, to understand how tricks performed.

### Some technical details

It uses Unity Mecanim animation system when mixing animations, but the root movement is scripted separately. Each kick animation contains information about which foot is best used for mixing (which one is more stable at end), so that the root movement is dynamic and predictable for determine the ball trajectory, which is based on physics with air resistance, but with slightly reduced gravity to give the player more time for reaction.

Animations are made using motion capture, but existing ones are for development only and will be replaced/reworked, and number of animations will be much larger. Normals on clothes are made dynamic to simulate folds when twisting the spine and raising legs.

Screen-switching effects are implemented as Scriptable Renderer Feature for URP, they have some settings that are randomized every time. So far there are two effects, it is planned to add a few more.