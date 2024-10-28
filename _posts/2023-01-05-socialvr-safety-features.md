---
title: SocialVR-Safety-Features
description: A research studying sexual harassment in social VR games and designing features to prevent them
author: Evan
date: 2023-01-05 12:00:00 +0800
categories: [Research, SocialVR]
tags: [social, vr, unity]
pin: true
image:
  path: /pictures/socialvr-logo.png
  alt: 'Logo for the SocialVR project (feature: personal bubble)'
---

# Introduction
Social Virtual Reality (VR) games offer immersive socialization experiences but pose challenges of increased and traumatizing harassment. Reactive approaches, such as reporting and moderation, respond to harassment after it happens. However, because of the difficulty in collecting evidence, lack of moderators, and the traumatic nature of embodied harassment, reactive solutions alone are not effective in the context of social VR.

In this study, we explore and redesign proactive and instant-reactive safety designs to mitigate harassment. Proactive designs aim to prevent or discourage harassment from occurring, while instant-reactive designs focus on minimizing harm during incidents. Based on prior design and literature, we approach proactive and instant-reactive designs with three approaches: personal bubble, clarifying social norms, and encouraging bystander intervention.

# Work
We developed and implemented safety features for a virtual reality (VR) application using the Unity Game Engine, the industry standard for VR development. Our target device was the Meta Quest 2 headset, chosen for its popularity among VR users and the ease of development afforded by its extensive community and documentation. We utilized the Meta XR All-in-One SDK package, which provided the necessary libraries to manage controller inputs, in-game interactions, and headset simulation.

To facilitate multiplayer connectivity, we employed the Photon Unity Networking (PUN) framework. Our implementation allows users to join a pre-existing non-local server hosted with PUN. This framework enabled us to monitor live player interactions and the Unity scene in real-time, which was crucial for triggering our various safety features based on in-game events.

We developed a personal bubble system utilizing Unity's built-in collision detection. Each player has three distinct colliders attached to trigger different effects upon proximity with another player:

- Hard Boundary: Functions as a trigger that calculates the speed of colliding players. If a player is moving toward another, a reverse velocity is applied to their rigid body, repelling them and ensuring that only active movement results in repulsion. This prevents misuse by stationary players.

- Soft Boundary: Simplifies interactions by disabling the mesh renderer of its components and temporarily deactivating hard boundaries, allowing unrestricted movement when appropriate.

We also established a suggestion system using the Photon Remote Procedure Call (RPC) mechanism. This allows players to send suggestions or feedback to specific individuals by transmitting data identified by Photon ViewIDs. Additionally, we implemented systems for blocking and abuse detection. The blocking mechanism uses a simple dictionary to track block statuses between players. While our initial abuse detection was basic, we plan to incorporate more sophisticated methods similar to cooldown systems found in modern password protections for enhanced security in future iterations.

Based on comprehensive user testing, we made several refinements:

- Safety Suggestions Button: Adjusted to always face the user, ensuring easy access regardless of other players' orientations.

- Scrollable Menu: Introduced to simplify the selection of nearby players when sending safety suggestions, enhancing usability.

- Personal Bubble Enhancement: Integrated with our badge system so that if a player breaches another's hard boundary while physical interactions are disabled, a visible blue sphere flashes momentarily. This visual cue represents the boundary's size and signals a request for personal space.

These enhancements ensure that users have a more intuitive and secure experience while interacting in the VR environment, addressing both functional requirements and user comfort.

![Desktop View](/pictures/socialvr-0.jpg)
![Desktop View](/pictures/socialvr-1.jpg)
