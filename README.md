# BARBAROS

**BARBAROS** is a performance-oriented, web-based operating system designed for
both desktop and mobile environments.

The system focuses on giving user space **as much safe access as possible to
kernel-level functionality** in order to fully benefit from kernel execution
speed, while keeping control and isolation intact.

---

## Goal

BARBAROS aims to combine:
- Kernel-level performance
- Safe user-space access
- A modern web-based user interface
- A development model that scales from desktop to mobile

The core idea is simple:

> User space should be able to use kernel power extensively,  
> without directly executing privileged code.

---

## Kernel Access Model

BARBAROS is built around a **syscall-driven design**.

User space does not access privileged instructions directly.
Instead, it reaches kernel functionality through syscalls that are designed to
be fast, explicit, and safe.

Syscalls are not treated as a minimal interface.
They are the **primary way user space interacts with the system**.

This approach allows user-space software to:
- Benefit from kernel-level execution speed
- Avoid duplicating low-level logic
- Remain isolated from direct privileged execution

---

## Lightweight Kernel Threads (LWKTs)

BARBAROS provides **Lightweight Kernel Threads (LWKTs)** as a core primitive.

The LWKT model is **inspired by Go's goroutine design**, adapting the idea of
cheap, lightweight execution units to kernel space.

LWKTs are kernel-managed execution units that user space can create and control
through syscalls.

They are designed to:
- Be cheap to create and destroy
- Have low scheduling overhead
- Use minimal stack and context
- Enable very high levels of concurrency

This allows user-space runtimes to achieve near kernel-level performance
without breaking safety or privilege boundaries.

---

## Web-Based System Interface

BARBAROS uses a **web-based interface** as its primary user interaction model.

- UI is written in HTML, CSS, and JavaScript (mostly WASM)
- The same UI model is used for desktop and mobile devices
- No traditional desktop environment is required

The operating system is accessed entirely through this web interface.

---

## JavaScript ↔ Native Bridge

BARBAROS exposes system functionality to the web UI using a
**JavaScript ↔ Native bridge**, inspired by **Wails**.

- JavaScript handles UI and user interaction
- System logic is implemented in **Go and C++**
- Native code communicates with the kernel exclusively via syscalls

JavaScript acts only as a control and presentation layer.

---

## Local and Remote Usage

BARBAROS is designed to work both locally and remotely.

- Local access works offline
- When online, the same running system can be accessed remotely
- Local usage does not consume network bandwidth
- Remote usage feels identical to local usage

---

## Platform Scope

- Initial target: **32-bit x86**
- Planned support: **x86_64**
- Single system design for desktop and mobile use cases

---

## Status

BARBAROS is in early development.
Design and interfaces may evolve over time.

---

## Philosophy

BARBAROS treats the kernel as a performance engine
and user space as its primary consumer.

The goal is not to hide kernel power,
but to expose it safely and make it usable.

**Kernel speed. Web interface. One system.**
