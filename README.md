# embedded-firmware-mastery# 
i🏆 10-Month Master Embedded Systems & Firmware Engineering Curriculum

> **Goal:** Complete a comprehensive, industry-grade career transition into Embedded Systems & Firmware Engineering over **10 months (43 weeks at 12–14 hours/week)**.
> **Certification Strategy:** Earn **4 major credentials** across 6 structured stages:
> 1. **Fastbit Driver Engineering Certificates** (Udemy / Fastbit Lab)
> 2. **Arm Education Professional Certificate** + **UT Austin Verified Certificates** (edX)
> 3. **Fastbit FreeRTOS & Bootloader Certificates** (Udemy / Fastbit Lab)
> 4. **CU Boulder Real-Time Embedded Systems Specialization Certificate** (Coursera)
> 5. **Enterprise Zephyr RTOS & Devicetree Porting**
> 6. **Modern Safety-Critical Embedded Rust & Embassy Async**
>
> **Engineering & Repository Management:** Monorepo Git Strategy, **Conventional Commits**, Feature Branching Workflow, **Host Unit Testing (Unity)**, **QEMU Emulation (`qemu-system-arm`)**, **CI/CD (GitHub Actions)**, **Static Analysis (Cppcheck)**, and **Hardware Signal Documentation (Saleae/Mermaid)**.

---

## 🐙 GitHub Repository Setup, Organization & Commit Strategy

### 1. Initial Repository Setup & Configuration
Set up a single production-grade monorepo named `embedded-firmware-mastery` on GitHub before starting Week 1:

* **Repository Initialization:**
  ```bash
    git init embedded-firmware-mastery
      cd embedded-firmware-mastery
        git branch -M main

         * Embedded C .gitignore Setup: Exclude build artifacts, binary images (.elf, .hex, .bin, .o), and IDE settings:
            # Build directories
            build/
            build-*/
            .ninja/

            # Binary outputs & object files
            *.elf
            *.hex
            *.bin
            *.o
            *.d

            # IDE & Toolchain files
            .vscode/
            .idea/
            *.ioc
            Debug/
            Release/

             * Branch Protection Rules: Configure GitHub branch protection on main requiring GitHub Actions CI checks to pass before merging PRs.
             2. Standardized Monorepo Directory Architecture
             embedded-firmware-mastery/
             ├── .github/
             │   ├── workflows/
             │   │   └── build-test.yml            # Automated CI/CD workflow (Build + Unity Tests + QEMU)
             │   └── ISSUE_TEMPLATE/               # Bug & feature request templates
             ├── stage-1-baremetal-drivers/
             │   ├── drivers/                      # Bare-metal GPIO, UART, SPI, I2C drivers (.c/.h)
             │   ├── tests/                        # Host C unit tests (Unity framework)
             │   └── CMakeLists.txt                # Host build system for unit tests
             ├── stage-2-cmsis-arm/
             │   ├── cmsis-drivers/                # CMSIS-compliant wrappers
             │   └── docs/logic-analyzer/          # Captured Saleae signal traces (.png)
             ├── stage-3-rtos-bootloader/
             │   ├── bootloader/                   # Custom UART bootloader source
             │   └── rtos-app/                     # FreeRTOS multi-threaded firmware
             ├── stage-4-capstone/
             │   ├── firmware/                     # Combined RTOS telemetry node
             │   └── docs/architecture.md          # Mermaid state machine diagrams
             ├── stage-5-zephyr-rtos/
             │   ├── app/                          # Zephyr application code (Kconfig & DTS)
             │   └── boards/                       # Custom Devicetree overlays
             ├── stage-6-rust-embassy/
             │   └── src/                          # no_std Rust embassy async firmware
             ├── tools/
             │   ├── arm-none-eabi-toolchain.cmake # CMake cross-compilation file
             │   └── cppcheck.supp                 # Static analysis suppression rules
             ├── .clang-format                     # Repository code formatting rules
             ├── CONTRIBUTING.md                   # Git branching & commit guidelines
             └── README.md                         # Master portfolio landing page & badges

             3. Scheduled Commit Cadence & Git Workflow Routine
             Follow a strict, professional branching and commit routine tied to your 12–14 hour weekly schedule:
             gitGraph
                commit id: "chore: init repo layout"
                   branch feat/stage-1-gpio
                      checkout feat/stage-1-gpio
                         commit id: "feat(gpio): add RCC register definitions"
                            commit id: "test(gpio): add Unity test for pin mask"
                               commit id: "docs(gpio): add circuit schematic"
                                  checkout main
                                     merge feat/stage-1-gpio id: "ci: PR #1 merged (all checks passed)"

                                     Weekly Commit Cadence (12–14 Hours / Week)
                                      * Monday – Thursday (Nightly 1.5h Sessions) — Local Feature Development:
                                         * Work on a dedicated feature branch (e.g., git checkout -b feat/stage-1-usart-driver).
                                            * Make granular daily commits as you write C register macros and unit tests.
                                             * Saturday Morning (4h Deep-Work Hardware Lab) — Signal Validation & Hardware Commits:
                                                * Test C code on ST Nucleo hardware using SWD/GDB or run QEMU headless emulation.
                                                   * Capture physical signal frames with Saleae Logic Analyzer.
                                                      * Commit captured traces and driver implementation: docs(uart): add 115200 baud signal capture.
                                                       * Sunday Morning (2.5h Code Review & PR Merge) — CI/CD & Main Branch Integration:
                                                          * Run auto-formatting: clang-format -i drivers/*.c drivers/*.h.
                                                             * Run static analysis: cppcheck --enable=all stage-1-baremetal-drivers/.
                                                                * Open Pull Request on GitHub to merge feat/... into main.
                                                                   * Verify GitHub Actions CI build, Unity tests, and QEMU execution pass green.
                                                                      * Squash & Merge PR into main and delete the feature branch.
                                                                      Conventional Commits Standard Specification
                                                                      Format all commit messages using the standard: type(scope): description
                                                                       * feat(gpio): New peripheral driver or system capability (e.g., feat(i2c): add DMA multi-byte transmit driver).
                                                                        * fix(uart): Resolving a bug or register setting error (e.g., fix(usart): correct baud rate prescaler calculation).
                                                                         * test(ring-buf): Adding or updating Unity unit tests (e.g., test(ring-buf): cover buffer overflow edge case).
                                                                          * docs(readme): Adding circuit schematics or Saleae logic traces (e.g., docs(spi): add SSD1306 signal trace).
                                                                           * refactor(timer): Code changes without altering hardware behavior (e.g., refactor(timer): simplify prescaler calculation).
                                                                            * ci(workflow): Updating GitHub Actions workflow scripts (e.g., ci: add qemu emulation step).
                                                                             * style(format): Formatting code with .clang-format (e.g., style: reformat GPIO driver according to LLVM spec).
                                                                             💳 Course Access, Platform & App Readiness Matrix
                                                                             | Stage & Weeks | Required Apps / Platforms | Access & Pricing Model | Action Items Before Stage Begins |
                                                                             |---|---|---|---|
                                                                             | Stage 1 (W1–8) | Udemy App / Web
                                                                             VS Code / QEMU / STM32CubeIDE | Paid: ~$15/course or Udemy Subscription | Create GitHub repo, configure .gitignore, .clang-format, and Unity test framework. |
                                                                             | Stage 2 (W9–17) | edX App / Web
                                                                             Saleae Logic 2 / OpenOCD | Free to Audit
                                                                             (~$149–$199 for Arm Cert) | Download ST Reference Manual (RM0368) and set up Saleae USB logic analyzer software. |
                                                                             | Stage 3 (W18–25) | Udemy App / Web
                                                                             SEGGER SystemView | Paid: ~$15/course or Udemy Subscription | Download SEGGER SystemView for RTOS kernel execution profiling. |
                                                                             | Stage 4 (W26–35) | Coursera App / Web
                                                                             WSL2 / Linux Terminal | Free to Audit
                                                                             (~$49/mo Coursera Subscription) | Set up WSL2 (Ubuntu) for POSIX pthread and rate-monotonic scheduling labs. |
                                                                             | Stage 5 (W36–40) | Zephyr SDK / West CLI
                                                                             VS Code / QEMU ARM | Free / Open Source
                                                                             (Linux Foundation) | Install Zephyr SDK, Python west meta-tool, and cmake toolchain. |
                                                                             | Stage 6 (W41–43) | Rustup / Cargo / Embassy | Free / Open Source
                                                                             (Rust Embedded WG) | Install Rust toolchain with target thumbv7em-none-eabihf for Cortex-M. |
                                                                             🛠️ Hardware, Tools & Software Checklist
                                                                             | Category | Recommended Tool / Specs | Primary Purpose | Approx. Cost |
                                                                             |---|---|---|---|
                                                                             | Development Board | ST Nucleo-F401RE or NUCLEO-F446RE | Primary ARM Cortex-M target board | ~$15 - $25 |
                                                                             | Debugger | Onboard ST-LINK V2-1 (SWD/JTAG) | Step-through GDB debugging and flashing | Included on Nucleo |
                                                                             | Logic Analyzer | 8-Channel 24MHz USB Logic Analyzer | Decoding UART, SPI, I2C protocol frames | ~$10 - $12 |
                                                                             | Emulator / Virtual MCU | QEMU (qemu-system-arm) & Renode | Running target ARM binaries in headless CI/CD & GDB debugging without board | Free / Open Source |
                                                                             | Testing Framework | Unity C Framework & CMock | Host-based unit testing on x86 PC | Free / Open Source |
                                                                             | Static Analysis | Cppcheck & .clang-format | Automated static code check & styling | Free / Open Source |
                                                                             | CI/CD Pipeline | GitHub Actions (gcc-arm-none-eabi) | Automated build & unit test integration | Free for GitHub public repos |
                                                                             📅 43-Week Master Stage-by-Stage Curriculum
                                                                             STAGE 1: Bare-Metal Driver Engineering (Weeks 1–8)
                                                                             🎯 Stage Target: Master C memory mechanics, write bare-metal peripheral drivers directly from datasheets, setup GitHub monorepo, and implement host unit tests with Unity.
                                                                             📜 Certifications Earned: Fastbit Embedded C & MCU1/MCU2 Certificates
                                                                             Week 1: Low-Level C Foundations, Git Repo Setup & Unity Unit Tests
                                                                              * Access / Pricing: Paid / Udemy Subscription | Fastbit Embedded C
                                                                               * Topics: Memory segments, pointer arithmetic, address casting, volatile keyword, bitwise masking.
                                                                                * GitHub Task: Initialize embedded-firmware-mastery repository on GitHub. Configure .gitignore for embedded C build artifacts.
                                                                                 * Engineering Practice: Set up Unity test framework. Write host-executable tests verifying bit-masking routines and ring buffer logic without hardware dependencies.
                                                                                  * Scheduled Commit: feat(setup): initialize monorepo structure and unity unit test framework
                                                                                  Week 2: ARM Cortex-M Core, Processor Modes & Code Formatting Rules
                                                                                   * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU1 Course
                                                                                    * Topics: Cortex-M4 registers (R0-R15), Thread vs Handler mode, MSP vs PSP stack pointers, Vector Table.
                                                                                     * GitHub Task: Create .clang-format file in repo root. Configure VS Code / IDE to auto-format C source on save.
                                                                                      * Scheduled Commit: style(cortex-m): format vector table and add .clang-format rules
                                                                                      Week 3: Toolchain, Linker Scripts, QEMU & GitHub Actions CI Setup
                                                                                       * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU1 Startup & Linker Section
                                                                                        * Topics: arm-none-eabi-gcc toolchain, startup.c, vector table initialization, writing .ld linker scripts, QEMU setup (qemu-system-arm).
                                                                                         * GitHub Task: Configure GitHub Actions workflow (.github/workflows/build-test.yml) to compile target C code and run virtual ARM binaries in QEMU on every push.
                                                                                          * Scheduled Commit: ci(workflow): add github actions build and test pipeline
                                                                                          Week 4: Interrupt Architecture & Static Analysis (Cppcheck)
                                                                                           * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU1 Interrupts
                                                                                            * Topics: NVIC controller, interrupt priorities, preemption vs sub-priority, tail-chaining.
                                                                                             * GitHub Task: Add cppcheck step to local CMake build files and GitHub Actions workflow.
                                                                                              * Scheduled Commit: feat(nvic): implement exti gpio interrupt driver with debouncing
                                                                                              Week 5: Clock Tree, Power & GPIO Driver Architecture
                                                                                               * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU1 GPIO Driver
                                                                                                * Topics: RCC clock tree, PLLs, prescalers, GPIO push-pull vs open-drain, pull-up/down setup.
                                                                                                 * GitHub Task: Create feature branch feat/stage-1-gpio-driver. Isolate GPIO register access behind HAL functions.
                                                                                                  * Scheduled Commit: feat(gpio): implement modular bare-metal gpio driver library
                                                                                                  Week 6: Serial Communication: USART Driver & Ring Buffer Unit Tests
                                                                                                   * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU1 USART Driver
                                                                                                    * Topics: Asynchronous framing, baud rate registers, status flags, interrupt-driven ring buffers.
                                                                                                     * GitHub Task: Write Unity unit tests for RX/TX circular ring buffers (overflow, underflow, pointer wrapping) executed on x86 PC.
                                                                                                      * Scheduled Commit: test(usart): add unity tests for circular rx/tx ring buffer
                                                                                                      Week 7: Synchronous Protocols: I2C Master Driver & State Machine Testing
                                                                                                       * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU1 I2C Driver
                                                                                                        * Topics: I2C START/STOP conditions, 7-bit addressing, ACK/NACK handling, clock stretching.
                                                                                                         * GitHub Task: Validate I2C frame generation logic using mock register structures in Unity test files.
                                                                                                          * Scheduled Commit: feat(i2c): implement bare-metal master driver for MPU6050 sensor
                                                                                                          Week 8: High-Speed Protocols: SPI Driver, DMA & Stage 1 PR Merge
                                                                                                           * Access / Pricing: Paid / Udemy Subscription | Fastbit MCU2 SPI & DMA
                                                                                                            * Topics: SPI CPOL/CPHA modes, full-duplex configuration, Direct Memory Access (DMA) channels.
                                                                                                             * GitHub Task: Open PR on GitHub merging feat/stage-1-drivers into main. Verify CI pipeline passes clean without warnings.
                                                                                                              * Scheduled Commit: feat(spi): implement dma frame-buffer stream driver for oled
                                                                                                              STAGE 2: Official Architecture & Hardware Interfacing (Weeks 9–17)
                                                                                                              🎯 Stage Target: Validate hardware architecture knowledge through official university/Arm courses and master hardware signal documentation.
                                                                                                              📜 Certifications Earned: Arm Education Professional Certificate + UT Austin Verified Certificates
                                                                                                              Week 9: UT Austin - Circuit Interfacing & Schematic Docs
                                                                                                               * Access / Pricing: Free to Audit / Paid for Verified Cert ($49) | UT Austin Embedded Systems edX
                                                                                                                * Topics & Practice: Switch/LED circuit design, Ohm's law, current sourcing/sinking, MCU I/O ports. Document KiCAD schematics.
                                                                                                                 * Scheduled Commit: docs(schematics): add kibad circuit schematic for LED matrix
                                                                                                                 Week 10: UT Austin - Analog-to-Digital Conversion (ADC)
                                                                                                                  * Access / Pricing: Free to Audit / Paid for Verified Cert ($49) | UT Austin edX Vol 1
                                                                                                                   * Topics & Practice: Nyquist theorem, ADC sampling rates, quantization noise, sensor processing. Write C unit tests.
                                                                                                                    * Scheduled Commit: test(adc): add unity tests for ADC voltage scaling equations
                                                                                                                    Week 11: UT Austin - Timers, PWM & Sound Generation
                                                                                                                     * Access / Pricing: Free to Audit / Paid for Verified Cert ($49) | UT Austin edX Vol 2
                                                                                                                      * Topics & Practice: Timer reload values, PWM duty cycles, DAC sound output. Capture logic analyzer traces of PWM.
                                                                                                                       * Scheduled Commit: docs(pwm): add logic analyzer capture of audio tone PWM
                                                                                                                       Week 12: Logic Analyzer Signal Traces & Documentation
                                                                                                                        * Access / Pricing: Free Tool | Saleae Logic 2 Download
                                                                                                                         * Topics & Practice: Capture physical UART, I2C, SPI timing frames; embed annotated .png signal captures in repo README.
                                                                                                                          * Scheduled Commit: docs(protocols): add saleae logic traces for I2C and SPI frames
                                                                                                                          Week 13: Advanced GDB Debugging, QEMU Remote & HardFault Analysis
                                                                                                                           * Access / Pricing: Free OpenOCD / QEMU Tools | QEMU System ARM Documentation
                                                                                                                            * Topics & Practice: OpenOCD & QEMU GDB servers (-s -S remote debugging), watchpoints, disassembly inspection, HardFault stack dumps.
                                                                                                                             * Scheduled Commit: feat(debug): add hardfault stack frame dump to usart log
                                                                                                                             Week 14: Arm Education - CMSIS-Core Architecture
                                                                                                                              * Access / Pricing: Free to Audit / Arm Cert ($149) | Arm Education Essentials edX
                                                                                                                               * Topics & Practice: CMSIS-Core standard, ARM assembly interworking, MPU configuration. Maintain CMSIS driver compliance.
                                                                                                                                * Scheduled Commit: refactor(cmsis): align core headers with ARM CMSIS v5 standard
                                                                                                                                Week 15: Arm Education - CMSIS-Driver & Serial Protocols
                                                                                                                                 * Access / Pricing: Free to Audit / Arm Cert ($149) | Arm Education Module 3-4
                                                                                                                                  * Topics & Practice: Standardized CMSIS-Driver APIs for USART, SPI, I2C; hardware abstraction layer best practices.
                                                                                                                                   * Scheduled Commit: test(cmsis-usart): add host unit tests for CMSIS uart wrapper
                                                                                                                                   Week 16: Arm Education - Practical Hardware Co-Design
                                                                                                                                    * Access / Pricing: Free to Audit / Arm Cert ($149) | Arm Practical Hardware edX
                                                                                                                                     * Topics & Practice: Sensor fusion, power management, system clocks, hardware-software co-design.
                                                                                                                                      * Scheduled Commit: feat(power): implement low-power sleep mode with RTC wake interrupt
                                                                                                                                      Week 17: Stage 2 Review & Arm + UT Austin Cert Exams
                                                                                                                                       * Access / Pricing: Verified Cert Submission | Arm Professional Exam Portal
                                                                                                                                        * Milestone Deliverable: Claim Arm Education Verified Professional Certificate and UT Austin Verified Certificates.
                                                                                                                                         * Scheduled Commit: docs(readme): add verified Arm Professional certificate badge
                                                                                                                                         STAGE 3: Production RTOS & Firmware Infrastructure (Weeks 18–25)
                                                                                                                                         🎯 Stage Target: Master multi-threaded preemptive scheduling, FreeRTOS synchronization primitives, and custom bootloader development.
                                                                                                                                         📜 Certifications Earned: Fastbit FreeRTOS & Bootloader Certificates
                                                                                                                                         Week 18: FreeRTOS Kernel Mechanics & Stack Profiling
                                                                                                                                          * Access / Pricing: Paid / Udemy Subscription | Fastbit FreeRTOS Course
                                                                                                                                           * Topics & Practice: Preemptive priority scheduling, Task Control Blocks (TCBs), stack allocation. Configure stack overflow hooks.
                                                                                                                                            * Scheduled Commit: feat(freertos): initialize kernel tasks and add stack overflow hook
                                                                                                                                            Week 19: Concurrency, Mutexes & SystemView Tracing
                                                                                                                                             * Access / Pricing: Paid / Udemy Subscription | Fastbit FreeRTOS Mutex Section
                                                                                                                                              * Topics & Practice: Critical sections, Mutexes vs Semaphores, Priority Inversion & Priority Inheritance. Profile with SEGGER SystemView.
                                                                                                                                               * Scheduled Commit: docs(freertos): add systemview trace logs for priority inheritance
                                                                                                                                               Week 20: Thread-Safe Queues & Message Unit Tests
                                                                                                                                                * Access / Pricing: Paid / Udemy Subscription | Fastbit FreeRTOS Queues
                                                                                                                                                 * Topics & Practice: Thread-safe message queues, Queue Sets, Event Groups, Direct-to-Task Notifications. Write Unity tests.
                                                                                                                                                  * Scheduled Commit: test(queue): add host unit tests for sensor telemetry queue struct
                                                                                                                                                  Week 21: Deferred Interrupt Handling & Software Timers
                                                                                                                                                   * Access / Pricing: Paid / Udemy Subscription | Fastbit FreeRTOS Timers
                                                                                                                                                    * Topics & Practice: Deferring ISR execution to daemon tasks, FreeRTOS software timer callbacks, tick hooks.
                                                                                                                                                     * Scheduled Commit: feat(rtos-timer): implement deferred interrupt processing thread
                                                                                                                                                     Week 22: Custom Bootloader Architecture & Memory Maps
                                                                                                                                                      * Access / Pricing: Paid / Udemy Subscription | Fastbit Custom Bootloader Course
                                                                                                                                                       * Topics & Practice: Internal Flash sector organization, flash erase/program APIs, Vector Table Relocation (VTOR).
                                                                                                                                                        * Scheduled Commit: docs(bootloader): define flash memory partitioning and VTOR layout
                                                                                                                                                        Week 23: Bootloader Flashing Routine & Host Python Script
                                                                                                                                                         * Access / Pricing: Paid / Udemy Subscription | Fastbit Bootloader Programming
                                                                                                                                                          * Topics & Practice: Host UART flashing protocol, binary payload writing, stack pointer reset, app jumps. Write host Python flasher.
                                                                                                                                                           * Scheduled Commit: feat(bootloader): write host python UART flasher tool
                                                                                                                                                           Week 24: System Safety, Watchdogs & CRC32 Unit Tests
                                                                                                                                                            * Access / Pricing: Paid / Udemy Subscription | Fastbit Bootloader Safety
                                                                                                                                                             * Topics & Practice: Independent Watchdog (IWDG), Window Watchdog (WWDG), CRC32 binary verification. Write unit test.
                                                                                                                                                              * Scheduled Commit: test(crc32): verify host and target CRC32 checksum algorithms
                                                                                                                                                              Week 25: Stage 3 Review & Fastbit Certifications
                                                                                                                                                               * Access / Pricing: Certificate Issuance | Fastbit Portal
                                                                                                                                                                * Milestone Deliverable: Claim Fastbit FreeRTOS and Custom Bootloader certificates.
                                                                                                                                                                 * Scheduled Commit: docs(readme): update repo status with stage 3 completion certs
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