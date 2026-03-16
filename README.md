# XRCore Training Toolkit

XRCore Training Toolkit is a modular framework for building guided XR training flows in Unity.

It is designed to work as a training layer on top of XRCore SDK, with scenario orchestration, modular validators, and user feedback systems (UI, highlight, and audio).

## Demo

Add your demo assets in:

- `media/demo.mp4`
- `media/demo.gif`

Then reference them here, for example:

`![Demo](media/demo.gif)`

## Key Features

- Modular training runtime (`XRTrainingScenario`, `XRTrainingStep`, `XRTrainingScenarioRunner`)
- Validator system (`IXRTrainingValidator`) with extensible conditions
- Event-driven integration with XRCore where available
- Training feedback layer (instructions, progress, highlights, audio)
- Sample industrial training demo scene

## Requirements

- Unity 2022+ or Unity 6
- XRCore SDK (required for full integrated workflow)

## Quick Start

1. Import XRCore SDK into your Unity project.
2. Import XRCore Training Toolkit.
3. Open the sample scene in `Assets/XRCoreTrainingToolkit/Samples/IndustrialTrainingDemo/Scene/`.
4. Press Play and run the guided steps.

## License

This repository is licensed under the MIT License.