# XRCore Training Toolkit

[![Unity](https://img.shields.io/badge/Unity-2022%2B%20%7C%20Unity%206-black)](https://unity.com/)
[![Category](https://img.shields.io/badge/XR-Training-blue)](#)
[![AI](https://img.shields.io/badge/AI-Assistant%20Flows-purple)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

XRCore Training Toolkit is a guided training layer for Unity XR built on top of [XRCore SDK](https://github.com/splibiplay/xrcore-sdk).

Where XRCore focuses on agent architecture (`perception -> events -> reasoning -> behaviour`), this toolkit adds structured scenarios, validator-driven progression, and clear user feedback for real-world training workflows.

## Demo

- Repository video: `TrainingToolkit_1.mp4`
- YouTube demo: [Watch full demo](https://www.youtube.com/watch?v=NmwTmtryts8&list=PLdX4Fo1P__hpMhe5PJsSRt3a8O02E0dr3&index=2)

```text
Look, grab and place a tool in XR,
guided step-by-step with instructions, highlighting and audio.
```

## Why XRCore Training Toolkit

Most XR training prototypes become difficult to scale because training logic is mixed directly into interaction scripts.

This toolkit separates responsibilities:

- XRCore handles runtime intelligence and event infrastructure.
- XR Training Toolkit handles scenarios, progression, validation, and training UX.

This enables reusable training flows by changing scenario data and validators instead of rewriting scene logic.

## Relationship with XRCore

This toolkit depends on XRCore and is intentionally distributed as an extension layer.

- XRCore provides:
  - `XRCoreEventBus` and runtime core systems,
  - perception/detection providers,
  - agent and reasoner architecture.
- XR Training Toolkit adds:
  - `XRTrainingScenario` and `XRTrainingStep`,
  - `XRTrainingScenarioRunner`,
  - `IXRTrainingValidator`-driven progression,
  - feedback UX (instruction panel, progress, highlight, audio),
  - no-code setup and runtime robustness tooling.

If XRCore is missing, setup validation and editor notices clearly report the dependency.

## Key Features

- **Scenario-driven training as data**
  - `XRTrainingScenario` / `XRTrainingStep` as reusable ScriptableObject content.
- **Modular validator system**
  - validators for focus, grab, and place with extensible custom validators.
- **No-code setup workflow**
  - setup wizard with one-click setup, fix, and validate actions.
- **Runtime reliability**
  - guard, diagnostics log/persistence, feature gates, and telemetry export.
- **Input compatibility**
  - input abstraction supporting both `Input Manager` and `Input System`.
- **Store-ready workflow support**
  - QA report export, profile JSON import/export, and showcase scene support.

## Requirements

- Unity 2022+ or Unity 6
- XR-ready Unity project (OpenXR / XRI as needed by your app)
- [XRCore SDK](https://github.com/splibiplay/xrcore-sdk) for full integration

## Installation

1. Install/import XRCore SDK.
2. Import XRCore Training Toolkit package.
3. Open the training scene in your Unity project.
4. Open `Tools -> XR Training Toolkit -> Setup Wizard`.
5. Run `One-Click Setup + Fix + Validate` and press Play.

## Example Interaction Flow

```text
User looks at target
        ↓
Detection / interaction event is generated
        ↓
XRCoreEventBus publishes the event
        ↓
XRTrainingScenarioRunner advances progression
        ↓
UI / highlight / audio feedback updates
```

## Use Cases

- Industrial training simulations
- XR onboarding experiences
- Guided maintenance/task workflows
- Fast XR product demos
- Training prototype production

## Documentation

Toolkit docs are included in the Unity package under:

```text
Assets/TrainingToolkit/Documentation/
```

XRCore docs:

- [XRCore SDK repository](https://github.com/splibiplay/xrcore-sdk)

## License

XRCore Training Toolkit is distributed under the MIT License.
See [LICENSE](LICENSE) for details.