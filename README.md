# ichibui_dos

`ichibui_dos` is a robust orchestration and control application for a robotic dispensing module designed for high-vibration commercial kitchen environments. It provides accurate portion control for a variety of ingredients, integrated with auxiliary I/O and a user-friendly kiosk interface.

## System Overview

The system is built on a **Tauri** framework, leveraging **Rust** for low-level hardware orchestration and **React (TypeScript)** for the user interface. It is engineered to maintain precision in challenging kitchen environments where mechanical vibration and heavy use are standard.

### Core Capabilities

- **Robotic Dispensing:** Orchestrates ingredient dispensing using motors and high-precision scales.
- **Hardware Orchestration:** Interfaces with Phidget scales, motor controllers, and photo-eye sensors for real-time process monitoring.
- **User Interactions:** Tailored UI for various user roles (Operator, Manager, Admin) to handle daily operation, maintenance, and cleaning.
- **Operational Safety:** Integrated hatch control and photo-eye monitoring to ensure safe dispensing cycles.
- **Data Logging:** Tracks all dispensing actions, cleaning cycles, and system states in a local SQLite database.

## Technology Stack

- **Backend:** [Rust](https://www.rust-lang.org/)
  - **Tauri v2:** Cross-platform application framework.
  - **Tokio:** Asynchronous runtime for concurrent hardware control.
  - **control-components:** Specialized library for interfacing with industrial hardware components.
  - **Rusqlite:** Local data persistence for logging and configuration.
- **Frontend:** [React](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
  - **Vite:** Fast frontend build tool.
  - **Tailwind CSS:** Utility-first styling for a responsive kiosk UI.
  - **Radix UI & Shadcn/UI:** High-quality accessible components.
  - **Kioskboard / Simple Keyboard:** On-screen input for industrial touchscreens.

## Repository Structure

```text
ichibui_dos/
├── src/                # React Frontend (TypeScript)
│   ├── components/     # UI components (Carousel, Input, UI primitives)
│   ├── App.tsx         # Main application routing and data fetching
│   ├── dispense-screen.tsx # Primary dispensing interface
│   └── settings-menu.tsx   # Maintenance and configuration UI
├── src-tauri/          # Rust Backend (Hardware Orchestration)
│   ├── src/
│   │   ├── ichibu.rs   # Core dispensing cycle orchestration
│   │   ├── dispense.rs # Dispensing motor and logic control
│   │   ├── hatch.rs    # Hatch actuator logic
│   │   ├── io.rs       # Low-level I/O (Scale, PhotoEye, Motor) initialization
│   │   ├── state.rs    # Global application state management
│   │   └── lib.rs      # Tauri command handlers and entry point
│   └── Cargo.toml      # Rust dependencies and configuration
└── tailwind.config.js  # UI styling configuration
```

## Development

### Prerequisites

- [Rust](https://www.rust-lang.org/tools/install)
- [Node.js](https://nodejs.org/) (v18+)
- [Tauri CLI](https://tauri.app/v1/guides/getting-started/prerequisites)

### Setup & Running

1.  **Install dependencies:**
    ```bash
    npm install
    ```

2.  **Run in development mode:**
    ```bash
    npm run tauri dev
    ```

3.  **Build the application:**
    ```bash
    npm run tauri build
    ```

## Hardware Integration

The system expects several hardware components to be connected:
- **Phidget Scale:** Used for weight-based portion control.
- **Motor Controller:** Drives the dispensing mechanism.
- **Photo-Eye Sensor:** Detects vessel placement to trigger or inhibit dispensing.
- **Hatch Actuator:** Controls the delivery opening.

Configuration for these components is typically found in `~/.config/ichibu/`.

---
*Developed for accurate, reliable portion control in commercial environments.*
