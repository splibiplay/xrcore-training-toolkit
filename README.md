# XRCore Training Toolkit

[![Unity](https://img.shields.io/badge/Unity-2022%2B%20%7C%20Unity%206-black)](https://unity.com/) [![Category](https://img.shields.io/badge/XR-Training-blue)](#) [![AI](https://img.shields.io/badge/AI-Assistant%20Flows-purple)](#) [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

XRCore Training Toolkit es una capa de **entrenamiento guiado** para Unity XR construida encima de [XRCore — AI Agent Framework for Unity XR](https://github.com/splibiplay/xrcore-sdk).

Donde XRCore resuelve la **arquitectura de agentes XR (percepción → eventos → razonamiento → comportamiento)**, XRCore Training Toolkit añade la capa que falta para muchos proyectos reales: **escenarios de entrenamiento estructurados, pasos, validaciones y feedback claro para el usuario final**.

---

## Demo

[▶ Ver demo completa en YouTube](https://www.youtube.com/watch?v=NmwTmtryts8&list=PLdX4Fo1P__hpMhe5PJsSRt3a8O02E0dr3&index=2)

```text
Mira, coge y coloca una herramienta en XR,
guiado paso a paso con instrucciones, highlight y audio.
```

---

## ¿Por qué XRCore Training Toolkit?

En muchos proyectos de formación XR pasa lo siguiente:

- Se montan escenas de demo muy específicas.
- La lógica de entrenamiento ("mira", "coge", "coloca", "pulsa el botón", etc.) queda mezclada con scripts de interacción.
- Cada nuevo flujo de entrenamiento implica duplicar escenas, prefabs y lógica ad hoc.

XRCore Training Toolkit propone otra aproximación:

- **Separar el "motor XR" (XRCore) de la lógica de entrenamiento**.
- Definir entrenamientos como **escenarios de datos** (`XRTrainingScenario` + `XRTrainingStep`).
- Describir reglas de validación como **validadores reutilizables** (`IXRTrainingValidator`).
- Conectar todo a una **capa de feedback** (UI, highlight, audio) que haga el entrenamiento entendible en segundos.

De esta forma puedes reutilizar el mismo motor de agente XR (XRCore) para múltiples proyectos, y solo cambiar **escenarios y validadores** para crear nuevos cursos XR.

---

## Relación con XRCore

XRCore Training Toolkit está diseñado explícitamente para trabajar junto a [XRCore SDK](https://github.com/splibiplay/xrcore-sdk):

- XRCore proporciona:
  - `XRCoreEventBus` (bus de eventos).
  - Proveedores de percepción (detección, visión, etc.).
  - Agentes (`XRGuideAgent`) y razonadores (rule engine, state machine, LLM...).
- XRCore Training Toolkit añade:
  - `XRTrainingScenario` y `XRTrainingStep` para definir flujos de entrenamiento.
  - `XRTrainingScenarioRunner` para orquestar los pasos.
  - `IXRTrainingValidator` y validadores listos para usar (mirar, coger, colocar).
  - Sistema de feedback (UI de instrucciones, progreso, estado del paso, audio, highlight).
  - Una demo industrial lista para grabar vídeo en segundos.

**Requisito:** para la experiencia completa necesitas importar también XRCore en el proyecto Unity. El toolkit puede funcionar de forma limitada sin XRCore, pero está pensado como complemento natural del framework base.

---

## Características principales

- **Escenarios de entrenamiento como datos**:
  - `XRTrainingScenario`: ScriptableObject que define la secuencia de pasos.
  - `XRTrainingStep`: título, instrucción, validadores, modo de validación (`Any` / `All`).

- **Sistema de validación modular (`IXRTrainingValidator`)**:
  - `ObjectFocusValidator`: valida cuando el usuario mira a un objeto objetivo.
  - `ObjectGrabValidator`: valida cuando el objeto ha sido cogido.
  - `ObjectPlaceValidator`: valida cuando el objeto se coloca en una zona concreta.
  - Posibilidad de crear validadores propios (por ejemplo, pulsar un botón, accionar una palanca, completar un procedimiento).

- **Integración con eventos XRCore (sin acoplamiento duro)**:
  - Un bridge interno escucha eventos de `XRCoreEventBus` por reflexión cuando XRCore está presente.
  - Si XRCore no está instalado, el toolkit sigue funcionando para la demo básica y muestra advertencias claras.

- **Capa de feedback para el usuario**:
  - `XRTrainingInstructionPanel`: muestra título, instrucción y progreso del step.
  - `XRTrainingProgressUI`: representa el progreso con texto y "dots".
  - `XRTrainingStepIndicator`: indica estado del paso (INACTIVE / ACTIVE / COMPLETED / ERROR).
  - `XRTrainingHighlightBehaviour`: resalta el objeto relevante.
  - `XRTrainingAudioFeedback`: reproduce audio de éxito/error.

- **UI lista para XR**:
  - Prefabs `XRTrainingUIPanel` y `XRTrainingUIPanel_XRDemo` con canvas en World Space.
  - `XRTrainingUIFollowCamera` mantiene el panel frente a la cámara XR.

- **Demo industrial lista para grabar**:
  - Escena de ejemplo donde el usuario: **mira**, **coge** y **coloca** una herramienta.
  - Bootstrap que monta cámara, entorno, UI y lógica de entrenamiento automáticamente.

---

## Requisitos

- Unity **2022+** o **Unity 6**.
- Proyecto configurado para XR (OpenXR, XR Interaction Toolkit, etc.).
- [XRCore SDK](https://github.com/splibiplay/xrcore-sdk) instalado en el proyecto para integración completa.

---

## Instalación

1. Instala **XRCore SDK** (desde la Asset Store o desde el repositorio [xrcore-sdk](https://github.com/splibiplay/xrcore-sdk)).
2. Importa el paquete **XRCore Training Toolkit** en tu proyecto Unity.
3. Abre la escena de demo:
   - `Assets/XRCoreTrainingToolkit/Samples/IndustrialTrainingDemo/Scene/Demo_Training_Basic.unity`
4. Pulsa **Play** y sigue las instrucciones en el panel de training.

---

## Flujo de interacción de ejemplo

```text
Usuario mira la herramienta
        ↓
Se genera un evento de percepción / interacción
        ↓
XRCoreEventBus (en XRCore) publica el evento
        ↓
XRTrainingScenarioRunner avanza el paso de entrenamiento
        ↓
La capa de feedback actualiza UI / highlight / audio

```

---

## Casos de uso

XRCore Training Toolkit está pensado para:

- **Simulaciones de entrenamiento industrial** (procedimientos paso a paso).
- **Onboarding XR** para nuevos usuarios o empleados.
- **Guiado de tareas en tiempo real** en entornos industriales o de mantenimiento.
- **Demos de producto XR** donde quieres mostrar rápidamente un flujo de trabajo.
- **Prototipos de formación XR** antes de invertir en contenido muy complejo.

---

## Documentación adicional

La documentación específica del toolkit (Quick Start, guía de escenarios, validadores, setup de demo, checklist de Asset Store) se encuentra en el paquete Unity en:

```text
Assets/XRCoreTrainingToolkit/Documentation/

```

Para entender la arquitectura base de agentes XR, revisa también la documentación de XRCore en:

- Repositorio: https://github.com/splibiplay/xrcore-sdk

---

## Licencia

XRCore Training Toolkit se distribuye bajo licencia **MIT**.

Consulta el archivo [LICENSE](LICENSE) para más detalles.