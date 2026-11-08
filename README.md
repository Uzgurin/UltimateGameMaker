

# 🌟 UltimateGameMaker

> The framework for creating first-person view games in Godot.

A modular toolkit with actors, components, an advanced player controller,
and UI systems — to help you build immersive FPS games faster.

---

## 📋 Requirements

| Requirement | Value |
|-------------|-------|
| **Godot Engine** | `4.7+` |
| **Renderer** | `Forward+` |
| **Language** | GDScript |
| **Platforms** | Windows · Linux · macOS |

---

## License

This project is **open source**.

See the [`LICENSE`](LICENSE) file for full terms.

---

## 🚀 Quick Start

1. **Download** or clone the repository.
2. **Copy** the framework into your Godot `4.7+` project.
3. **Enable** the plugin in `Project → Project Settings → Plugins`.
4. **Run** the demo scene to see actors and components in action.

> Make sure your project uses the **Forward+** renderer:
> `Project Settings → Rendering → Renderer → Forward+`.

---
# Features

This framework will add modules, logic, a player, and mobs to the project that will help you in creating your game.

| Module | Discription |
|----------|-----------------------------------------------------------------|
| Settings | 	Framework settings |
| Config | 	Game configuration system for saving settings and other parameters |
| UIAudio | A module for flexible control of interface sounds |
| Game | 	The core module that streamlines level loading and management |
| InteractRay | A raycast for interacting with the interactive environment |
| ItemHandler | A module that lets you grab and hold items in your hands|
| GlobalSignals | Global signal manager |
| UIController | An interface controller that makes it quick and easy to switch between UI menus, change backgrounds, and display dialog windows |
| UINavBar | 	An extension to UIController that adds a dynamic navigation menu |
| InGameUI | A module for managing the in-game interface (hints, post-processing, etc.) |
| Manager | A global yet empty module where you can write custom logic for your game and work with other modules |


# In-Game Logic: Actors and Components

To build in-game logic, two new types of nodes are introduced — **actors** and **components**.

## Actors

**Actors** are nodes that directly participate in the game. As a rule, they have collision. The player interacts with them, and the main signals originate from them.


## Components

**Components** are nodes that allow you to create logic without a single line of code. All logic is based on the interaction of actors and components connected by signals.

## Example of Use

Thanks to these nodes, you can build complex chains of logic. For example:

**ShapeTrigger (Actor) → FunctionCaller (Component) → AnimationPlayer**

The player touches the trigger → the trigger sends a signal to the component to call a function → the component calls a method on `AnimationPlayer`.

This logic can be extended by adding new actors and components to the chain.

# Actors

| Actor | Description |
|-------|-------------|
| **BookSystem** | A system for creating interactive books |
| **DoorSystem** | A system for creating doors |
| **CassetteSystem** | A system for implementing cassette-based logic. Works only with `ItemHandler` |
| **ValveSystem** | A system for creating valves |
| **InteractiveAction** | A static object that sends a signal when the player hovers the cursor over it and presses |
| **Looker** | A static object that sends a signal if the player looks at it for `n` time |
| **ShapeTrigger** | Sends a signal when the player, an item, or a mob crosses its boundary or exits it |
| **UseInteractItem** | A static object that sends a signal if the player has a certain item. It can also change the behavior of the item itself |

# Components

| Component | Description |
|-----------|-------------|
| **ConsolePrint** | Outputs a message to the console |
| **EnvironmentSwitcher** | Allows flexible changing of the environment (`WorldEnvironment`, `VoxelGI`) |
| **Follower** | Receives a sequence of signals and, if it is correct, sends a signal. Suitable for code locks |
| **FunctionCaller** | Calls a method on a specified node or module. |
| **GameHint** | Shows an in-game hint. Works only with `UIController` |
| **Hider** | Hides or removes an object on the scene |
| **LevelStarter** | Called at the very beginning of the game, spawns the player. Allows you to create an introductory cutscene |
| **MaterialParamChanger** | Changes material parameters. Useful, for example, for creating a flashlight — it allows you to change the material's glow parameter |
| **Starter** | Sends a signal at the very beginning of the game |
| **Switcher** | Works as a switch. When receiving a signal, it returns a signal depending on the state (on/off) |
| **Timer** | Receives a signal, waits `n` time, and sends another signal |
| **Twiner** | Creates an object animation based on `Tween` |
| **Visibler** | Shows or loads an object |

# Player

The framework implements an advanced first-person player controller system, extensible via an addon system. The player serves as a flexible foundation: it provides a state manager (e.g., `STATE_CONTROL`, `STATE_ROTATING_VALVE`, etc.) and a movement state manager (`MOVE_STATE_IDLE`, `MOVE_STATE_WALK`, `MOVE_STATE_CROUCH`, etc.).

The framework already includes basic player addons:

| Addon | Description |
|-----------|-------------|
| **HeadBobber** | Advanced camera bobbing while walking |
| **Lean** | Head lean system |
| **Zoom** | Zoom-in |
| **Dyspnea** | Shortness of breath and slowdown while running |
| **Footstep** | Footprint and footstep sound system. Works in tandem with a footstep sounds script that is applied to static objects to play walking sounds. Supports automatic detection of wet surfaces (roughness map on the material) |
| **Looker** | Required for the Looker actor to function |
| **MotionBlur** | Adds blur when the camera rotates |
| **DofBlur** | Changes camera sharpness depending on distance |
