# ⚡ 10-Month Embedded Systems & Firmware Master Plan

> 43 Weeks • 12–14 Hours/Week | Integrated with Git Monorepo, QEMU Emulation, Zephyr RTOS & Rust Embassy

## Overview

**Goal:** Complete a comprehensive, industry-grade transition into Embedded Systems & Firmware Engineering over 10 months.

**Certification Strategy:** Earn 4 major credentials across 6 structured stages:

1. Fastbit Driver Engineering Certificates (Udemy / Fastbit Lab)
2. Arm Education Professional Certificate + UT Austin Verified Certificates (edX)
3. Fastbit FreeRTOS & Bootloader Certificates (Udemy / Fastbit Lab)
4. CU Boulder Real-Time Embedded Systems Specialization Certificate (Coursera)
5. Enterprise Zephyr RTOS & Devicetree Porting
6. Modern Safety-Critical Embedded Rust & Embassy Async

**Engineering & Repository Management:** Monorepo Git Strategy, Conventional Commits, Feature Branching Workflow, Host Unit Testing (Unity), QEMU Emulation (`qemu-system-arm`), CI/CD (GitHub Actions), Static Analysis (Cppcheck), and Hardware Signal Documentation (Saleae / Mermaid).

---

## Dashboard

- 43 Weeks — Duration
- 12–14 Hrs — Weekly effort
- 6 Stages — Roadmap
- Zephyr + Rust — Advanced RTOS

**Master Curriculum Progress:** 0% Completed (0/43 Weeks)

```text
████████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ 0%
```

---

## 🥇 Stage 1: Bare-Metal Driver Engineering (Weeks 1–8)

> Certificates: Fastbit C & MCU1/MCU2

### Week 1: Low-Level C Foundations, Git Repo Setup & Unity Suite
- Access: Paid / Udemy Subscription
- Tags: Git Setup, Unity Test Framework
- Topics: Pointers, raw physical address casting, `volatile`, section alignment (`.text`, `.data`, `.bss`, stack, heap).
- GitHub Task: Initialize the `embedded-firmware-mastery` monorepo on GitHub and configure `.gitignore`.
- Scheduled Commit: `feat(setup): initialize monorepo structure and unity unit test framework`
- Study Here: [Fastbit Embedded C Course](https://www.udemy.com/course/microcontroller-embedded-c-programming/)

### Week 2: ARM Cortex-M Core & Code Formatting Rules
- Access: Paid / Udemy Subscription
- Tags: Conventional Commit, `.clang-format`
- Topics: Cortex-M4 registers (R0-R15), Thread vs Handler mode, MSP vs PSP, vector table layout.
- GitHub Task: Create a repo-root `.clang-format` file and enforce standard C formatting.
- Scheduled Commit: `style(cortex-m): format vector table and add .clang-format rules`
- Study Here: [Fastbit MCU1 Course](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/)

### Week 3: Toolchain, Linker Scripts, QEMU & GitHub Actions CI
- Access: Paid / Udemy Subscription
- Tags: GitHub Actions CI, QEMU Emulation
- Topics: `arm-none-eabi-gcc`, `startup.c`, vector table init, `.ld` linker scripts, `qemu-system-arm`.
- GitHub Task: Configure GitHub Actions workflow to compile C code and run ARM binaries under QEMU on every push.
- Scheduled Commit: `ci(workflow): add github actions build and test pipeline`
- Study Here: [Fastbit Startup & Linker Section](https://fastbitlab.com/)

### Week 4: Interrupt Architecture & Static Analysis
- Access: Paid / Udemy Subscription
- Tags: Cppcheck Analysis
- Topics: NVIC structures, interrupt preemption, sub-priority, latency, tail-chaining.
- GitHub Task: Integrate `cppcheck` static analysis into the local build and GitHub Actions workflow.
- Scheduled Commit: `feat(nvic): implement exti gpio interrupt driver with debouncing`
- Study Here: [Fastbit MCU1 Interrupts](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/)

### Week 5: Clock Tree, Power & GPIO Driver HAL
- Access: Paid / Udemy Subscription
- Tags: Feature Branch
- Topics: RCC clock tree, PLLs, prescalers, GPIO push-pull vs open-drain, pull-up/down.
- GitHub Task: Create a feature branch such as `feat/stage-1-gpio-driver` and isolate GPIO register access behind HAL functions.
- Scheduled Commit: `feat(gpio): implement modular bare-metal gpio driver library`
- Study Here: [Fastbit GPIO Driver Section](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/)

### Week 6: USART Driver & Ring Buffer Unit Tests
- Access: Paid / Udemy Subscription
- Tags: Unity Unit Tests
- Topics: Asynchronous framing, baud-rate registers, status flags, interrupt-driven ring buffers.
- GitHub Task: Write Unity tests for RX/TX circular ring buffers executed on x86 PC.
- Scheduled Commit: `test(usart): add unity tests for circular rx/tx ring buffer`
- Study Here: [Fastbit USART Driver Section](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/)

### Week 7: I2C Master Driver & State Machine Unit Tests
- Access: Paid / Udemy Subscription
- Tags: Mock Register Tests
- Topics: I2C START/STOP conditions, 7-bit addressing, ACK/NACK, clock stretching.
- GitHub Task: Validate I2C frame generation logic using mock register structures in Unity tests.
- Scheduled Commit: `feat(i2c): implement bare-metal master driver for MPU6050 sensor`
- Study Here: [Fastbit I2C Driver Section](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/)

### Week 8: SPI Driver, DMA & Stage 1 PR Merge
- Access: Paid / Udemy Subscription
- Tags: Pull Request Merge
- Topics: SPI CPOL/CPHA, full-duplex, DMA channels.
- GitHub Task: Open a PR merging `feat/stage-1-drivers` into `main` and verify CI passes cleanly.
- Scheduled Commit: `feat(spi): implement dma frame-buffer stream driver for oled`
- Study Here: [Fastbit MCU2 SPI & DMA](https://www.udemy.com/course/mastering-microcontroller2-with-peripherals/)

---

## 🥈 Stage 2: Official Architecture & Hardware Interfacing (Weeks 9–17)

> Certificates: Arm Professional + UT Austin

### Week 9: UT Austin - Circuit Interfacing & Schematic Docs
- Access: Free to Audit
- Tags: Schematic Docs
- Topics: Switch/LED circuit design, Ohm’s law, MCU I/O ports. Document KiCAD schematics in the repo.
- Scheduled Commit: `docs(schematics): add kibad circuit schematic for LED matrix`
- Study Here: [UT Austin Embedded Systems edX](https://users.ece.utexas.edu/~valvano/edX/)

### Week 10: UT Austin - Analog-to-Digital Conversion (ADC)
- Access: Free to Audit
- Tags: ADC Math Tests
- Topics: Nyquist theorem, ADC sampling, quantization noise. Write C unit tests for raw-to-voltage math.
- Scheduled Commit: `test(adc): add unity tests for ADC voltage scaling equations`
- Study Here: [UT Austin edX Vol 1](https://www.edx.org/course/embedded-systems-shape-the-world-microcontroller-i)

### Week 11: UT Austin - Timers, PWM & Sound Generation
- Access: Free to Audit
- Tags: PWM Signal Capture
- Topics: Timer reload values, PWM duty cycles, DAC sound output. Capture logic traces of PWM frequency.
- Scheduled Commit: `docs(pwm): add logic analyzer capture of audio tone PWM`
- Study Here: [UT Austin edX Vol 2](https://www.edx.org/course/embedded-systems-shape-the-world-multi-threaded-i)

### Week 12: Logic Analyzer Signal Traces & Documentation
- Access: Free Tool
- Tags: Logic Traces (.png)
- Topics: Capture physical UART, I2C, SPI timing frames and document annotated signal captures.
- Scheduled Commit: `docs(protocols): add saleae logic traces for I2C and SPI frames`
- Study Here: [Saleae Logic 2 Downloads](https://www.saleae.com/downloads/)

### Week 13: Advanced GDB Debugging, QEMU Remote & HardFault Handler
- Access: Free OpenOCD / QEMU
- Tags: Stack Frame Dumps
- Topics: OpenOCD and QEMU GDB servers (`-s -S`), watchpoints, disassembly inspection, HardFault stack dumps.
- Scheduled Commit: `feat(debug): add hardfault stack frame dump to usart log`
- Study Here: [OpenOCD & QEMU Documentation](https://openocd.org/doc/html/index.html)

### Week 14: Arm Education - CMSIS-Core Architecture
- Access: Free to Audit
- Tags: Arm Cert ($149)
- Topics: CMSIS-Core standard, ARM assembly interworking, MPU configuration.
- Scheduled Commit: `refactor(cmsis): align core headers with ARM CMSIS v5 standard`
- Study Here: [Arm Education Essentials edX](https://www.edx.org/professional-certificate/armeducationx-embedded-systems-essentials)

### Week 15: Arm Education - CMSIS-Driver & Serial Protocols
- Access: Free to Audit
- Tags: CMSIS Wrapper Tests
- Topics: Standardized CMSIS-Driver APIs for USART, SPI, I2C; hardware abstraction best practices.
- Scheduled Commit: `test(cmsis-usart): add host unit tests for CMSIS uart wrapper`
- Study Here: [Arm Education Module 3-4](https://www.edx.org/professional-certificate/armeducationx-embedded-systems-essentials)

### Week 16: Arm Education - Practical Hardware Co-Design
- Access: Free to Audit
- Tags: Power Profiling
- Topics: Sensor fusion, power management, system clocks, hardware-software co-design.
- Scheduled Commit: `feat(power): implement low-power sleep mode with RTC wake interrupt`
- Study Here: [Arm Practical Hardware edX](https://www.edx.org/course/getting-practical-with-hardware)

### Week 17: Stage 2 Review & Arm + UT Austin Cert Exams
- Access: Certificate Milestone
- Topics: Complete the Arm and UT Austin certificate process and update the README badges.
- Scheduled Commit: `docs(readme): add verified Arm Professional certificate badge`
- Study Here: [edX Arm Professional Certificate](https://www.edx.org/professional-certificate/armeducationx-embedded-systems-essentials)

---

## 🥉 Stage 3: Production RTOS & Firmware Infrastructure (Weeks 18–25)

> Certificates: Fastbit FreeRTOS & Bootloader

### Week 18: FreeRTOS Kernel Mechanics & Stack Hook
- Access: Paid / Udemy Subscription
- Tags: Stack Overflow Hook
- Topics: Preemptive scheduling, TCBs, stack allocation, stack overflow hooks.
- Scheduled Commit: `feat(freertos): initialize kernel tasks and add stack overflow hook`
- Study Here: [Fastbit FreeRTOS Course](https://www.udemy.com/course/mastering-freertos-hands-on-with-cortex-m-microcontrollers/)

### Week 19: Concurrency, Mutexes & SystemView Tracing
- Access: Paid / Udemy Subscription
- Tags: SystemView Traces
- Topics: Mutexes vs Semaphores, Priority Inheritance. Profile contention with SEGGER SystemView.
- Scheduled Commit: `docs(freertos): add systemview trace logs for priority inheritance`
- Study Here: [Fastbit FreeRTOS Mutex Section](https://www.udemy.com/course/mastering-freertos-hands-on-with-cortex-m-microcontrollers/)

### Week 20: Thread-Safe Queues & Message Unit Tests
- Access: Paid / Udemy Subscription
- Tags: Queue Unit Tests
- Topics: Thread-safe message queues, Event Groups, queue semantics.
- Scheduled Commit: `test(queue): add host unit tests for sensor telemetry queue struct`
- Study Here: [Fastbit FreeRTOS Queues](https://www.udemy.com/course/mastering-freertos-hands-on-with-cortex-m-microcontrollers/)

### Week 21: Deferred Interrupt Handling & Software Timers
- Access: Paid / Udemy Subscription
- Topics: Deferred ISR execution to daemon tasks, software timers, ISR latency.
- Scheduled Commit: `feat(rtos-timer): implement deferred interrupt processing thread`
- Study Here: [Fastbit FreeRTOS Timers](https://fastbitlab.com/)

### Week 22: Custom Bootloader Architecture & Memory Maps
- Access: Paid / Udemy Subscription
- Tags: Memory Map Docs
- Topics: Internal flash sector organization, VTOR relocation, flash partitioning.
- Scheduled Commit: `docs(bootloader): define flash memory partitioning and VTOR layout`
- Study Here: [Fastbit Custom Bootloader Course](https://www.udemy.com/course/short-course-on-bootloader-development/)

### Week 23: Bootloader Flashing Routine & Host Python Script
- Access: Paid / Udemy Subscription
- Tags: Python Flasher
- Topics: Host UART flashing protocol, binary payload writing, stack-pointer reset, app jumps.
- Scheduled Commit: `feat(bootloader): write host python UART flasher tool`
- Study Here: [Fastbit Bootloader Programming](https://fastbitlab.com/)

### Week 24: System Safety, Watchdogs & CRC32 Unit Tests
- Access: Paid / Udemy Subscription
- Tags: CRC32 Testing
- Topics: Independent Watchdog, Window Watchdog, CRC32 verification.
- Scheduled Commit: `test(crc32): verify host and target CRC32 checksum algorithms`
- Study Here: [Fastbit Bootloader Safety](https://fastbitlab.com/)

### Week 25: Stage 3 Review & Fastbit Certifications
- Access: Certificate Milestone
- Topics: Update README badges with Fastbit FreeRTOS and Bootloader completion.
- Scheduled Commit: `docs(readme): update repo status with stage 3 completion certs`
- Study Here: [Fastbit Portal](https://fastbitlab.com/)

---

## 🎓 Stage 4: Academic Real-Time Systems Theory & Capstone (Weeks 26–35)

> Certificate: CU Boulder Specialization (4 Courses)

### Week 26: CU Boulder Course 1 - RMS & POSIX pthreads
- Access: Free to Audit
- Tags: POSIX Lab
- Topics: Rate Monotonic Scheduling, POSIX threads, Linux/WSL2 execution.
- Scheduled Commit: `feat(posix-rt): implement rate monotonic pthread scheduling lab`
- Study Here: [CU Boulder Course 1](https://www.coursera.org/learn/real-time-embedded-systems-concepts-practices)

### Week 27: CU Boulder Course 1 - Real-Time Linux & Jitter
- Access: Free to Audit
- Tags: Linux Timing Scripts
- Topics: Clock resolution, PREEMPT_RT, timing measurement, jitter analysis.
- Scheduled Commit: `test(jitter): add timing measurement scripts for pthread execution`
- Study Here: [CU Boulder Course 1 Modules 3-4](https://www.coursera.org/learn/real-time-embedded-systems-concepts-practices)

### Week 28: CU Boulder Course 2 - Dynamic Priority (EDF & LLF)
- Access: Free to Audit
- Tags: EDF Simulator
- Topics: Earliest Deadline First, Least Laxity First, utilization bounds.
- Scheduled Commit: `feat(edf-sim): implement host C simulator for EDF scheduling feasibility`
- Study Here: [CU Boulder Course 2](https://www.coursera.org/learn/real-time-embedded-systems-theory-analysis)

### Week 29: CU Boulder Course 2 - Priority Inversion & PCP
- Access: Free to Audit
- Tags: PCP Unit Tests
- Topics: Priority Ceiling Protocol, Priority Inheritance, deadlock prevention.
- Scheduled Commit: `test(deadlock): add unity tests for priority ceiling protocol logic`
- Study Here: [CU Boulder Course 2 Modules 3-4](https://www.coursera.org/learn/real-time-embedded-systems-theory-analysis)

### Week 30: CU Boulder Course 3 - Flash File Systems & ECC
- Access: Free to Audit
- Tags: ECC Unit Tests
- Topics: Flash wear leveling, ECC memory (SECDED), Hamming correction.
- Scheduled Commit: `test(ecc): add unit tests for SECDED hamming error correction`
- Study Here: [CU Boulder Course 3](https://www.coursera.org/learn/real-time-mission-critical-systems-design)

### Week 31: CU Boulder Course 3 - Fail-Safe Systems
- Access: Free to Audit
- Tags: Mermaid State Machine
- Topics: Redundancy, watchdog loops, fail-safe rollback state machines.
- Scheduled Commit: `docs(fail-safe): document system rollback state machine in mermaid`
- Study Here: [CU Boulder Course 3 Modules 3-4](https://www.coursera.org/learn/real-time-mission-critical-systems-design)

### Week 32: Capstone Phase 1 - Architecture Setup
- Access: Independent Lab
- Tags: CMake Targets
- Topics: Architecture decomposition for bootloader + telemetry node, build targets.
- Scheduled Commit: `feat(capstone): initialize capstone project build configuration`
- Study Here: [CU Boulder Capstone Course](https://www.coursera.org/learn/real-time-embedded-systems-capstone)

### Week 33: Capstone Phase 2 - Multi-Threaded Telemetry Core
- Access: Independent Lab
- Tags: Cppcheck Analysis
- Topics: Sensor task, OLED display task, UART CLI thread, static analysis scans.
- Scheduled Commit: `feat(capstone): integrate multi-threaded sensor and oled telemetry core`

### Week 34: Capstone Phase 3 - Fault Recovery & Traces
- Access: Independent Lab
- Tags: Saleae Traces
- Topics: Stack high-water mark profiling, watchdog recovery, stress testing traces.
- Scheduled Commit: `docs(capstone): add saleae logic traces under maximum CPU telemetry load`

### Week 35: Portfolio Publishing & Certificate Collection
- Access: Final Master Credential
- Topics: Polish README, architecture diagrams, build badges, and portfolio landing page.
- Scheduled Commit: `docs(readme): finalize capstone documentation and portfolio landing page`
- Study Here: [Coursera Specialization Final Portal](https://www.coursera.org/specializations/real-time-embedded-systems)

---

## 🚀 Stage 5: Enterprise Zephyr RTOS & Devicetree (Weeks 36–40)

> Industry Focus: Enterprise IoT & Nordic/NXP

### Week 36: Zephyr Architecture, `west` Build Tool & Devicetree
- Access: Free / Open Source
- Tags: West CLI & DTS
- Topics: Linux Foundation model, Kconfig, Devicetree (`.dts` / `.overlay`), `west` meta-tool.
- Scheduled Commit: `feat(zephyr): setup west workspace and devicetree overlay for Nucleo board`
- Study Here: [Zephyr RTOS Docs](https://docs.zephyrproject.org/latest/)

### Week 37: Zephyr Kernel Primitives (Threads & Workqueues)
- Access: Free / Open Source
- Tags: `k_work` & `k_thread`
- Topics: Threads, workqueues, ISR offloading, mutexes, semaphores.
- Scheduled Commit: `feat(zephyr): implement multi-threaded telemetry pipeline using k_work queues`
- Study Here: [Zephyr Kernel APIs](https://docs.zephyrproject.org/latest/kernel/index.html)

### Week 38: Zephyr HAL & Sensor Drivers
- Access: Free / Open Source
- Tags: `DEVICE_DT_GET`
- Topics: Device driver API model, I2C/SPI sensor bindings, power management.
- Scheduled Commit: `feat(zephyr-drivers): implement I2C and SPI sensor drivers via Devicetree bindings`
- Study Here: [Zephyr Driver Model](https://docs.zephyrproject.org/latest/services/device_mgmt/index.html)

### Week 39: Zephyr Shell CLI & Logging Subsystem
- Access: Free / Open Source
- Tags: Zephyr Shell Subsystem
- Topics: Shell CLI, asynchronous logging, CTF tracing.
- Scheduled Commit: `feat(zephyr-shell): add custom terminal debugging commands via Zephyr shell`
- Study Here: [Zephyr Logging & Shell](https://docs.zephyrproject.org/latest/services/shell.html)

### Week 40: Zephyr Network Stack / BLE & QEMU CI Integration
- Access: Free / Open Source
- Tags: QEMU Cortex-M3 Target
- Topics: BLE host/controller split, QEMU execution, automation.
- Scheduled Commit: `ci(zephyr): add native Zephyr QEMU automated build and test pipeline`
- Study Here: [Zephyr QEMU Support](https://docs.zephyrproject.org/latest/boards/qemu/cortex_m3/doc/index.html)

---

## 🦀 Stage 6: Modern Safety-Critical Embedded Systems with Rust / Embassy (Weeks 41–43)

> Industry Focus: Next-Gen Automotive & Safety-Critical

### Week 41: Bare-Metal Rust Foundations (`no_std`) & PAC/HAL
- Access: Free / Open Source
- Tags: `no_std` Rust
- Topics: Ownership, embedded lifetimes, Peripheral Access Crates (PAC), HAL abstractions.
- Scheduled Commit: `feat(rust): initialize no_std bare-metal rust crate for Cortex-M`
- Study Here: [Embedded Rust Book](https://docs.rust-embedded.org/book/)

### Week 42: Embassy Async Framework & Hardware Interrupts
- Access: Free / Open Source
- Tags: Async Embassy Executor
- Topics: Async GPIO/UART interrupts, executor model, zero-cost abstractions.
- Scheduled Commit: `feat(embassy): implement async UART driver using embassy executor`
- Study Here: [Embassy Async Book](https://embassy.dev/book/)

### Week 43: Final 10-Month Master Portfolio Consolidation
- Access: Portfolio Milestone
- Topics: Finalize README, architecture diagrams, badges, and complete portfolio index.
- Scheduled Commit: `docs(readme): publish complete 10-month master embedded systems portfolio`
- Study Here: [GitHub](https://github.com/)

---

## 🐙 GitHub Repository Setup, Architecture & Commit Routine

### 1. Initial Monorepo Setup & Branch Protection

```bash
git init embedded-firmware-mastery
cd embedded-firmware-mastery
git branch -M main
```

Example `.gitignore` for embedded C projects:

```gitignore
# Build directories
build/
build-*/
.ninja/

# Binary outputs and object files
*.elf
*.hex
*.bin
*.o
*.d

# IDE and toolchain files
.vscode/
.idea/
*.ioc
Debug/
Release/
```

### 2. Standardized Monorepo Directory Architecture

```text
embedded-firmware-mastery/
├── .github/
│   ├── workflows/
│   │   └── build-test.yml            # CI/CD workflow: build + Unity + QEMU
│   └── ISSUE_TEMPLATE/               # Bug and feature request templates
├── stage-1-baremetal-drivers/
│   ├── drivers/                      # Bare-metal GPIO, UART, SPI, I2C drivers
│   ├── tests/                        # Host C unit tests (Unity)
│   └── CMakeLists.txt                # Host test build config
├── stage-2-cmsis-arm/
│   ├── cmsis-drivers/                # CMSIS-compliant wrappers
│   └── docs/logic-analyzer/          # Saleae signal traces (.png)
├── stage-3-rtos-bootloader/
│   ├── bootloader/                   # Custom UART bootloader source
│   └── rtos-app/                     # FreeRTOS multi-threaded firmware
├── stage-4-capstone/
│   ├── firmware/                     # Combined RTOS telemetry node
│   └── docs/architecture.md          # Mermaid state machine diagrams
├── stage-5-zephyr-rtos/
│   ├── app/                          # Zephyr app code (Kconfig + DTS)
│   └── boards/                       # Custom Devicetree overlays
├── stage-6-rust-embassy/
│   └── src/                          # no_std Rust Embassy async firmware
├── tools/
│   ├── arm-none-eabi-toolchain.cmake # Cross-compilation file
│   └── cppcheck.supp                 # Static analysis suppressions
├── .clang-format                     # Repository style rules
├── CONTRIBUTING.md                   # Git branching and commit policy
├── README.md                         # Master portfolio landing page
└── .gitignore                        # Embedded build exclusions
```

### 3. Scheduled Commit Cadence & Git Workflow Routine

Follow a strict, professional branching and commit cadence that matches the 12–14 hour weekly plan.

```text
gitGraph
  commit id: "chore: init repo layout"
    branch feat/stage-1-gpio
      checkout feat/stage-1-gpio
      commit id: "feat(gpio): add RCC register definitions"
      commit id: "test(gpio): add Unity test for pin mask"
      commit id: "docs(gpio): add circuit schematic"
    checkout main
    merge feat/stage-1-gpio id: "ci: PR #1 merged (all checks passed)"
```

#### Weekly cadence
- Monday–Thursday: feature development in dedicated branch work sessions
- Saturday morning: hardware validation and signal captures
- Sunday morning: code review, formatting, static analysis, PR merge

### 4. Conventional Commit Standards

Use the standard format: `type(scope): description`

- `feat(gpio)`: new peripheral driver or system capability
- `fix(usart)`: resolve a bug or register calculation issue
- `test(ring-buf)`: add or update Unity unit tests
- `docs(readme)`: documentation, schematics, traces, or portfolio work
- `refactor(timer)`: no behavior change, structural cleanup
- `ci(workflow)`: update GitHub Actions or build automation
- `style(format)`: format code via `.clang-format`

---

## 💳 Course Access, Platform & App Readiness Matrix

| Stage & Weeks | Required Apps / Platforms | Access & Pricing Model | Action Items Before Stage Begins |
|---|---|---|---|
| Stage 1 (W1–8) | Udemy App / Web, VS Code, QEMU, STM32CubeIDE | Paid: ~$15/course or Udemy subscription | Create the GitHub repo, configure `.gitignore`, `.clang-format`, and Unity framework. |
| Stage 2 (W9–17) | edX App / Web, Saleae Logic 2, OpenOCD | Free to Audit; ~$149–$199 for Arm cert | Download ST reference manuals and install Saleae Logic 2. |
| Stage 3 (W18–25) | Udemy App / Web, SEGGER SystemView | Paid / subscription | Install SystemView for RTOS kernel profiling. |
| Stage 4 (W26–35) | Coursera App / Web, WSL2, Linux Terminal | Free to Audit; ~$49/mo Coursera subscription | Set up WSL2 for POSIX pthread labs and rate-monotonic scheduling exercises. |
| Stage 5 (W36–40) | Zephyr SDK / West CLI, VS Code, QEMU ARM | Free / Open Source | Install Zephyr SDK, Python `west`, and the CMake toolchain. |
| Stage 6 (W41–43) | Rustup / Cargo / Embassy | Free / Open Source | Install the Rust toolchain with `thumbv7em-none-eabihf`. |

## 🛠️ Hardware, Tools & Software Checklist

| Category | Recommended Tool / Specs | Primary Purpose | Approx. Cost |
|---|---|---|---|
| Development Board | ST Nucleo-F401RE or NUCLEO-F446RE | Primary ARM Cortex-M target | ~$15–$25 |
| Debugger | Onboard ST-LINK V2-1 (SWD/JTAG) | GDB debugging and flashing | Included on Nucleo |
| Logic Analyzer | 8-channel 24MHz USB Logic Analyzer | Decode UART, SPI, I2C timing | ~$10–$12 |
| Emulator / Virtual MCU | QEMU (`qemu-system-arm`) & Renode | Headless ARM execution and GDB debugging | Free / Open Source |
| Testing Framework | Unity C Framework & CMock | Host-based unit testing on x86 PC | Free / Open Source |
| Static Analysis | Cppcheck & `.clang-format` | Automated static checking and code style | Free / Open Source |
| CI/CD Pipeline | GitHub Actions + `gcc-arm-none-eabi` | Automated build and test integration | Free on public GitHub repos |

---

## ⚙️ Professional Firmware Engineering & QEMU CI/CD

### Automated GitHub Actions Workflow (`.github/workflows/build-test.yml`)

```yaml
name: Firmware Build, Test & Emulation Pipeline

on: [push, pull_request]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Install ARM Toolchain & Build Dependencies
        run: |
          sudo apt-get update
          sudo apt-get install -y gcc-arm-none-eabi gcc cmake ninja-build cppcheck qemu-system-arm

      - name: Run Host C Unit Tests (Unity Framework)
        run: |
          mkdir -p build-tests && cd build-tests
          cmake -DBUILD_TESTS=ON ..
          make && ctest --output-on-failure

      - name: Run Cppcheck Static Analysis
        run: |
          cppcheck --enable=all --suppress=missingIncludeSystem stage-1-baremetal-drivers/

      - name: Build Bare-Metal ARM Firmware Binaries
        run: |
          mkdir -p build-firmware && cd build-firmware
          cmake -DCMAKE_TOOLCHAIN_FILE=../tools/arm-none-eabi-toolchain.cmake ..
          make

      - name: Execute ARM Binary in QEMU Emulation
        run: |
          qemu-system-arm -M stm32vldiscovery \
            -kernel build-firmware/firmware.bin \
            -nographic \
            -icount shift=7,align=off,sleep=off \
            -device loader,file=build-firmware/firmware.bin
```

This workflow keeps the project professional, reproducible, and CI-validated for each stage of the roadmap.

---

## Final Notes

This curriculum intentionally blends:

- Bare-metal embedded C mastery
- ARM architecture and CMSIS understanding
- RTOS and bootloader engineering
- Real-time scheduling theory
- Zephyr ecosystem practice
- Modern embedded Rust and Embassy async development

The repository is structured to behave like a portfolio-grade embedded systems monorepo, not just a course notebook.

                                                                                                                                                                 STAGE 4: Academic Real-Time Theory & Capstone Portfolio (Weeks 26–35)
                                                                                                                                                                 🎯 Stage Target: Master formal real-time scheduling theory (RMS, EDF), POSIX threads, and build a capstone portfolio piece.
                                                                                                                                                                 📜 Certifications Earned: CU Boulder Real-Time Embedded Systems Specialization Certificate (4 Courses)
                                                                                                                                                                 Week 26: CU Boulder Course 1 - Rate Monotonic Scheduling & POSIX
                                                                                                                                                                  * Access / Pricing: Free to Audit / Coursera ($49/mo) | CU Boulder Course 1
                                                                                                                                                                   * Topics & Practice: Rate Monotonic (RM) scheduling theory, POSIX threads (pthreads), Linux user vs kernel real-time.
                                                                                                                                                                    * Scheduled Commit: feat(posix-rt): implement rate monotonic pthread scheduling lab
                                                                                                                                                                    Week 27: CU Boulder Course 1 - Real-Time Linux & Constraints
                                                                                                                                                                     * Access / Pricing: Free to Audit / Coursera ($49/mo) | CU Boulder Course 1 Mod 3-4
                                                                                                                                                                      * Topics & Practice: Hard vs soft real-time constraints, clock resolution, clock_gettime, PREEMPT_RT. Write timing scripts.
                                                                                                                                                                       * Scheduled Commit: test(jitter): add timing measurement scripts for pthread execution
                                                                                                                                                                       Week 28: CU Boulder Course 2 - Dynamic Priority Scheduling (EDF & LLF)
                                                                                                                                                                        * Access / Pricing: Free to Audit / Coursera ($49/mo) | CU Boulder Course 2
                                                                                                                                                                         * Topics & Practice: Earliest Deadline First (EDF), Least Laxity First (LLF), processor utilization bounds. Build host C simulator.
                                                                                                                                                                          * Scheduled Commit: feat(edf-sim): implement host C simulator for EDF scheduling feasibility
                                                                                                                                                                          Week 29: CU Boulder Course 2 - Priority Inversi

## Prerequisites & Toolchain Setup
To compile and emulate ARM Cortex-M firmware locally or in GitHub Codespaces, install the following system dependencies:
bash
sudo apt-get update
sudo apt-get install -y gcc-arm-none-eabi qemu-system-arm

