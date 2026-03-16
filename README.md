# XRCore Training Toolkit

[![Unity](https://img.shields.io/badge/Unity-2022%2B%20%7C%20Unity%206-black)](https://unity.com/) [![Category](https://img.shields.io/badge/XR-Training-blue)](#) [![AI](https://img.shields.io/badge/AI-Assistant%20Flows-purple)](#) [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

XRCore Training Toolkit is a **guided training layer** for Unity XR built on top of [XRCore — AI Agent Framework for Unity XR](https://github.com/splibiplay/xrcore-sdk).

Where XRCore focuses on the **agent architecture (perception → events → reasoning → behaviour)**, XRCore Training Toolkit adds what many real projects are missing: **structured training scenarios, steps, validators, and clear user feedback**.

---

## Demo

[▶ Watch full demo on YouTube](https://www.youtube.com/watch?v=NmwTmtryts8&list=PLdX4Fo1P__hpMhe5PJsSRt3a8O02E0dr3&index=2)

```text
Look, grab and place a tool in XR,
guided step-by-step with instructions, highlighting and audio.
```

---

## Why XRCore Training Toolkit?

In many XR training projects, the pattern is always the same:

- Demo scenes are built for one very specific flow.
- Training logic ("look", "grab", "place", "press the button"…) is mixed with interaction scripts.
- Every new training flow means duplicating scenes, prefabs and ad-hoc logic.

XRCore Training Toolkit proposes a different approach:

- **Separate the XR engine (XRCore) from the training logic**.
- Define trainings as **data scenarios** (`XRTrainingScenario` + `XRTrainingStep`).
- Express validation rules as **reusable validators** (`IXRTrainingValidator`).
- Connect everything to a **feedback layer** (UI, highlight, audio) that makes the training understandable in seconds.

This lets you reuse the same XR agent engine (XRCore) across multiple projects and build new XR courses by changing **scenarios and validators**, not by rewriting low-level interaction code.

---

## Relationship with XRCore

XRCore Training Toolkit is explicitly designed to work together with [XRCore SDK](https://github.com/splibiplay/xrcore-sdk):

- XRCore provides:
  - `XRCoreEventBus` (event bus).
  - Perception providers (detection, vision, etc.).
  - Agents (`XRGuideAgent`) and reasoners (rule engine, state machine, LLM…).
- XRCore Training Toolkit adds:
  - `XRTrainingScenario` and `XRTrainingStep` to define training flows.
  - `XRTrainingScenarioRunner` to orchestrate step progression.
  - `IXRTrainingValidator` and ready-to-use validators (look, grab, place).
  - A feedback system (instruction UI, progress, step state, audio, highlight).
  - An industrial-style demo ready to record in seconds.

**Requirement:** for the full experience you should also import XRCore into the Unity project. The toolkit can run a limited demo without XRCore, but it is designed as a natural companion to the core framework.

---

## Key Features

- **Training scenarios as data**
  - `XRTrainingScenario`: ScriptableObject defining the sequence of steps.
  - `XRTrainingStep`: title, instruction, validators, validation mode (`Any` / `All`).

- **Modular validation system (`IXRTrainingValidator`)**
  - `ObjectFocusValidator`: succeeds when the user looks at a target object.
  - `ObjectGrabValidator`: succeeds when the object has been grabbed.
  - `ObjectPlaceValidator`: succeeds when the object is placed in a target zone.
  - Easy to extend with custom validators (e.g. press a button, operate a lever, complete a checklist).

- **Integration with XRCore events (no hard coupling)**
  - An internal bridge listens to `XRCoreEventBus` events via reflection when XRCore is present.
  - If XRCore is missing, the toolkit still runs the basic demo and logs clear warnings.

- **User feedback layer**
  - `XRTrainingInstructionPanel`: shows step title, instruction and progress.
  - `XRTrainingProgressUI`: renders step progress with text and dots.
  - `XRTrainingStepIndicator`: shows step state (INACTIVE / ACTIVE / COMPLETED / ERROR).
  - `XRTrainingHighlightBehaviour`: highlights the relevant object.
  - `XRTrainingAudioFeedback`: plays success / error audio cues.

- **XR-ready UI**
  - Prefabs `XRTrainingUIPanel` and `XRTrainingUIPanel_XRDemo` using World Space canvases.
  - `XRTrainingUIFollowCamera` keeps the panel comfortably in front of the XR camera.

- **Industrial demo ready to record**
  - Example scene where the user **looks at**, **grabs**, and **places** a tool.
  - Bootstrap logic that assembles camera, environment, UI and training logic automatically.

---

## Requirements

- Unity **2022+** or **Unity 6**.
- Project configured for XR (OpenXR, XR Interaction Toolkit, etc.).
- [XRCore SDK](https://github.com/splibiplay/xrcore-sdk) installed for full integration.

---

## Installation

1. Install **XRCore SDK** (from the Asset Store or the [xrcore-sdk](https://github.com/splibiplay/xrcore-sdk) repository).
2. Import the **XRCore Training Toolkit** package into your Unity project.
3. Open the demo scene:
   - `Assets/XRCoreTrainingToolkit/Samples/IndustrialTrainingDemo/Scene/Demo_Training_Basic.unity`
4. Press **Play** and follow the on-screen training instructions.

---

## Example Interaction Flow

```text
User looks at the tool
        ↓
A perception / interaction event is generated
        ↓
XRCoreEventBus (in XRCore) publishes the event
        ↓
XRTrainingScenarioRunner advances the training step
        ↓
The feedback layer updates UI / highlight / audio

```

---

## Use Cases

XRCore Training Toolkit is designed for:

- **Industrial training simulations** (step-by-step procedures).
- **XR onboarding** for new users or employees.
- **Real-time task guidance** in industrial or maintenance environments.
- **XR product demos** where you need to show a workflow quickly.
- **XR training prototypes** before investing in heavy content production.

---

## Additional Documentation

Toolkit-specific documentation (Quick Start, Scenario Guide, Validators Guide, Demo Setup, Asset Store Checklist) ships inside the Unity package at:

```text
Assets/XRCoreTrainingToolkit/Documentation/

```

For a deeper understanding of the underlying agent architecture, see the XRCore docs:

- Repository: https://github.com/splibiplay/xrcore-sdk

---

## License

XRCore Training Toolkit is distributed under the **MIT License**.

See the [LICENSE](LICENSE) file for full details.