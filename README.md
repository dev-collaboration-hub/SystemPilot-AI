# SystemPilot AI

**SystemPilot AI** is a lightweight, completely offline Windows assistant designed to prevent Cursor from freezing by intelligently managing CPU, memory, disk usage, and background processes.

It runs locally on the CPU and does not send system information to the cloud.

## Problem

Cursor may freeze or respond slowly when the system is under heavy resource pressure. This can cause:

* Slow typing
* Delayed code completion
* Unresponsive windows
* High CPU or memory usage
* Disk overload
* System-wide lag

SystemPilot AI detects these conditions and applies safe optimizations to keep Cursor responsive.

## Main Features

* Monitor CPU, memory, and disk usage
* Detect Cursor and related processes
* Identify resource-heavy background applications
* Give Cursor higher process priority when required
* Safely limit selected background processes
* Automatically manage resources through Coding Mode
* Provide an offline AI chat interface
* Store preferences and action history locally
* Restore original process settings

## Example Conversation

```text
User: Cursor is freezing.

AI: Memory usage is at 91%, and a background application is consuming
significant resources.

Would you like me to temporarily reduce its priority?

User: Yes.

AI: The background application's priority has been reduced.
Cursor should now become more responsive.
```

## Core Principles

* Completely offline
* CPU-only
* Lightweight
* No cloud APIs
* Privacy-friendly
* Permission required before risky actions
* Transparent and reversible system changes
* Reliable system control without depending on a language model

## Architecture

```text
Chat Interface
      ↓
Intent Engine
      ↓
Safety and Permission Layer
      ↓
Decision Engine
      ↓
Resource Monitor
      ↓
Windows Process Controller
```

The system controller will be deterministic. An optional language model may understand conversations, but it will never control Windows directly.

## Offline AI

The default version will use a lightweight intent engine to understand commands such as:

```text
Enable Coding Mode.
Why is Cursor freezing?
How much memory is Cursor using?
Reduce background CPU usage.
Restore the original settings.
Which application is using the most memory?
```

A tiny CPU-only language model may be added later for more natural conversations. The core controller will continue working without it.

## Technology

* Python 3
* Python standard library
* Windows APIs and PowerShell
* Tkinter desktop interface
* JSON or SQLite for local storage
* Optional `llama.cpp` integration

The core system will not require third-party Python packages.

## Safety Rules

SystemPilot AI will:

* Never terminate an application without permission
* Never disable antivirus or Windows Security
* Save original process settings before changing them
* Restore settings when Coding Mode is disabled
* Show every action and its reason
* Keep a local action history
* Reject dangerous system commands

## Development Roadmap

### Milestone 1 — Resource Monitor

* Read CPU, memory, and disk usage
* List running processes
* Detect Cursor and related processes
* Display a live command-line summary

### Milestone 2 — Safe Process Controller

* Read process priority and CPU affinity
* Safely change process priority
* Apply temporary CPU affinity limits
* Restore original settings
* Add action logging and error handling

### Milestone 3 — Decision Engine

* Define resource-pressure levels
* Detect sustained overload
* Rank processes by resource consumption
* Recommend safe optimizations
* Prevent rapid or repeated setting changes

### Milestone 4 — Offline Chat Engine

* Implement intent detection
* Understand system questions and commands
* Extract application names and action parameters
* Generate clear responses
* Add confirmation flows

### Milestone 5 — Coding Mode

* Prioritize Cursor and development tools
* Limit selected background workloads
* React automatically to resource pressure
* Restore normal settings safely
* Support configurable preferences

### Milestone 6 — Desktop Interface

* Build a lightweight Tkinter chat window
* Display current resource usage
* Add Coding Mode controls
* Show recommendations and completed actions
* Provide settings and activity history

### Milestone 7 — Optional Tiny Local Model

* Add optional CPU-only model support
* Keep the model disabled by default
* Restrict the model to conversation and intent assistance
* Measure memory usage and response time
* Provide a fallback to the built-in intent engine

### Milestone 8 — Testing and Release

* Add unit and integration tests
* Test restoration after crashes
* Measure the application’s resource overhead
* Package the application for Windows
* Write installation and usage documentation

## Performance Targets

* Less than 100 MB of idle memory usage without the optional model
* Negligible CPU usage while idle
* Configurable monitoring interval between 1 and 10 seconds
* Fast local command processing
* No internet connection required
* All resource changes must be reversible

## Proposed Project Structure

```text
systempilot-ai/
├── systempilot/
│   ├── monitoring/
│   ├── processes/
│   ├── decision/
│   ├── chat/
│   ├── safety/
│   ├── memory/
│   └── ui/
├── tests/
├── examples/
├── docs/
├── config.example.json
├── LICENSE
└── README.md
```

## Platform Support

The first version will support:

* Windows 10
* Windows 11

Linux and macOS support may be considered later.

## Project Status

SystemPilot AI is currently in the planning and early development stage. Development will begin with **Milestone 1 — Resource Monitor**.
