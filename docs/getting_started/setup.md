---
layout: default
title: Setup
parent: Getting Started
nav_order: 2
permalink: /getting_started/setup
---

# Setup

---

## Installation
To work with VE, the directory named "VanillaEvents" (the folder must be named exactly like this) must be placed in the ```datapacks``` folder like a regular datapack. Then the ```/reload``` command is used to reload the datapacks. VE should install automatically and then print a success message.

{: .warning }
> To make VE work, it must be executed **before** all other datapacks. This is necessary because otherwise datapacks executed before VE can no longer access the events or behave unexpectedly.
> To achieve this, the datapack will disable itself on each reload and then re-enable itself, this time at the first position in the execution order.
> To avoid unexpected behavior, care should be taken that other datapacks use the ```datapack enable``` command in their load function only conditionally (cooldown or run once). Otherwise unpredictable behavior or reload loops may occur.

If VanillaEvents was only installed as a dependency for another datapack, you are now done. Have fun!

If you want to develop a datapack using the features of VanillaEvents, continue with the next section.

## Register Events
If you have found an interesting event in the [Events Category](/VEDocs/events) and you want your datapack to perform certain actions when the event is triggered, it is important to tell VE that you want to use the event. VE itself keeps track of all datapacks and the events that are needed. So VE always checks only the events that are needed.

To enable/register an event, use the following command, ideally in your load function.
```scoreboard players add VESys.EVENTNAME 1```

Replace EVENTNAME with the case sensitive name mentioned in the events documentation.
For example: PlayerMoveEvent, BatToggleSleepEvent, PlayerMovementStateTransitionEvent.

