# Navigation Component Documentation

This document provides architectural guidelines, API references, and best practices for integrating the core **Navigation Component** into application workflows.

## Table of Contents
- [Architecture Overview](#architecture-overview)
- [Defining Navigation Graphs](#defining-navigation-graphs)
- [Deep Linking](#deep-linking)
- [Best Practices](#best-practices)

---


## Architecture Overview

The system architecture consists of three fundamental building blocks working together to manage app state and visual transitions:

1. **Navigation Graph**: A centralized XML or JSON resource asset containing all individual screens (destinations) and connected paths (actions).
2. **NavHost**: A structural container UI element injected into the activity layout that swaps destinations out dynamically.
3. **NavController**: The programmatic controller obj that manages the active stack, processes transition events, and executes navigation requests.

---

## Defining Navigation Graphs

Below is a declarative snippet outlining how destinations are linked via unique action targets.

```json
{
  "graphId": "main_nav_graph",
  "startDestination": "home_screen",
  "destinations": {
    "home_screen": {
      "type": "Fragment",
      "actions": {
        "action_home_to_details": "details_screen"
      }
    },
    "details_screen": {
      "type": "Fragment",
      "arguments": {
        "itemId": "String"
      }
    }
  }
}
```

---

## Deep Linking

The controller intercepts external intents and reconstructs a proper backstack history automatically.

* **Explicit Deep Links**: Triggered programmatically via notification actions using a pending intent sequence.
* **Implicit Deep Links**: Defined via specific pattern strings inside your navigation configurations:

```xml
<deepLink app:uri="www.example.com/details/{itemId}" />
```

---

## Best Practices

- [x] Centralize all graph layouts instead of scattering cross-screen intents.
- [x] Type-check bundle parameters using custom safe arguments compile plugins.
- [ ] Implement abstract navigation interfaces to keep screens decoupled from platform routing classes.
