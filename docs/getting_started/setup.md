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
> In order for VE to fully function, it must be executed **before** all other datapacks. This is necessary because otherwise certain datapacks can no longer access the events or behave unexpectedly.

> To achieve this, the datapack will disable itself on each reload and then re-enable itself, this time at the first position in the execution order.

> To avoid unexpected behavior, care should be taken that other datapacks use the ``datapack enable`` command in their load function only conditionally (cooldown or run once). Otherwise unpredictable behavior or reload loops may occur.