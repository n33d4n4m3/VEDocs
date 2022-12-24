---
layout: default
title: Introduction
parent: Getting Started
nav_order: 1
permalink: /getting_started/introduction
---

# Introduction

---

VanillaEvents is intended to be a datapack that assists other developers in developing a datapack. It's designed as a dependency pack, which by itself does not add functionality to the game, but it collects and provides useful information, which other datapacks need to function. The datapack works with so-called *events*, which are conditionally fired in every tick of the game. Here, the datapack strictly follows its role model, the [Bukkit API](https://github.com/Bukkit/Bukkit).

## Events?
Did you move? Did you attack a cow? Did you go to sleep? It's planned that each of these actions will trigger an event in the VanillaEvents datapack. An event is a short temporary state that is triggered depending on the event's destination. Since VanillaEvents should always be the first datapack to execute in a gametick, other datapacks can now access this information, evaluate details and even modify it in some cases.

## Example
Let's suppose you want to check in the datapack you are developing whether the player is looking up while climbing a ladder. If he doesn't look up, you want the movement to be stopped.

If you have VanillaEvents installed in your world and the PlayerMoveEvent is enabled, you can implement exactly this task with an Oneliner.
```
execute as @e[tag=VE.PlayerMoveEvent] if score @s VEGbl.thePlayer.currentMovementState matches 5 if score @s VE.PlayerMoveEvent.hasClimbed matches 1 unless score @s VE.PlayerMoveEvent.toPitch matches -9000 run scoreboard players set @s VE.PlayerMoveEvent.willModify 1
```

| Command part                                                  | explanation                                                           |
|:--------------------------------------------------------------|:----------------------------------------------------------------------|
| @e[tag=VE.PlayerMoveEvent]                                    | Select all players with an fired PlayerMoveEvent (the player moved)   |
| if score @s VEGbl.thePlayer.currentMovementState matches 5    | Only select the players with the Movement State 5 (Climbing)          |
| if score @s VE.PlayerMoveEvent.hasClimbed matches 1           | Check if the player has a higher Y-Coord than before                  |
| unless score @s VE.PlayerMoveEvent.toPitch matches -9000      | Check if the player doesn't look straight up                          |
| scoreboard players set @s VE.PlayerMoveEvent.willModify 1     | Modify the event (teleport the player to his pre-event location)      |


