# CPU Benchmark Workbench Release Files

This folder contains packaged source archives for **CPU Benchmark Workbench**.

## Packages documented here

This document now keeps the earlier **v24** release information, the newer **v26** graph update information, and the latest **v27** update information together.

---

## v24 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v24.zip`  
**Program version:** `24.0.0`

CPU Benchmark Workbench is a Windows desktop benchmark application for testing CPU performance across multiple workload types, including:

- Integer and bit-manipulation workloads
- Floating-point workloads
- SIMD workloads
- AVX2 / FMA workloads when supported
- AVX-512 workloads when supported
- AES acceleration workloads when supported
- Memory and cache behavior
- Matrix math
- Prime-number scanning
- Mandelbrot compute
- Smart thread scaling
- Burn-in runs
- Overall system scoring
- Best-use-case analysis based on benchmark results

### What is inside the zip

The zip is intended for people who want to **open, build, and modify the project in Visual Studio**.

Typical contents include:

- `CpuBenchmarkWorkbench.sln`
- `src/CpuBenchmarkWorkbench/`
- C# source files
- project file
- license and documentation files

### Requirements to compile

To build this project, you should have:

- **Windows 10 or Windows 11**
- **Visual Studio 2026**
  - Community, Professional, or Enterprise edition is fine
- **.NET 8 SDK**
- Visual Studio workload:
  - **.NET desktop development**

Recommended:

- latest Visual Studio 2026 updates installed
- latest .NET 8 updates installed

### How to compile

1. Download and extract `CpuBenchmarkWorkbench_Windows11_VisualStudio_v24.zip`
2. Open `CpuBenchmarkWorkbench.sln` in **Visual Studio 2026**
3. Let Visual Studio restore dependencies if prompted
4. Select:
   - **Debug** or **Release**
   - **x64** preferred
5. Build the solution:
   - **Build > Build Solution**
6. Run it:
   - **Debug > Start Without Debugging**
   - or press **Ctrl+F5**

### Runtime notes

The program is a Windows Forms desktop application built for modern .NET on Windows.

Depending on how it is built and published, users may need:

- **.NET 8 Desktop Runtime**

If building directly in Visual Studio with the included project, the proper runtime and SDK should be enough.

The main application window is designed to start in a maximized state for easier viewing on large displays and high-core-count benchmark systems.

### CPU feature support

The benchmark suite detects available CPU features and only enables certain tests when supported by the system and runtime.

Examples include:

- SSE / SSE2 / SSE3
- SSSE3
- SSE4.1 / SSE4.2
- AVX
- AVX2
- FMA
- AES
- AVX-512 families when available
- NUMA-related system reporting and placement-aware execution

Because some features depend on both **hardware support** and **runtime exposure**, the exact test list may vary between systems.

### Smart Sweep behavior

The **Smart Sweep** mode does not test every thread count from 1 to maximum.

Instead, it automatically samples:

- 1 thread
- 25%
- 50%
- 75%
- 100%

Example on a 48-thread system:

- 1
- 12
- 24
- 36
- 48

This gives a much faster scaling picture without excessive test time.

### Burn-In mode

The program also includes a **Burn-In Run** mode for longer stress-style benchmark cycling.

Use it to:

- run selected tests repeatedly
- observe sustained performance
- compare behavior over time
- check stability during long workloads

### Overall scoring

At the end of a completed benchmark session, CPU Benchmark Workbench can produce an **overall system score**.

Scoring features include:

- A normalized score range from **0 to 100,000**
- Weighted scoring across benchmark families
- Reduced sensitivity to a single extreme outlier result
- Better representation of overall CPU capability across mixed workloads

The score is intended to give a practical high-level summary of the system’s benchmark performance rather than replace detailed per-test analysis.

### Best use case analysis

After a run completes, the program also provides an opinion about the system’s strongest likely use case based on the benchmark profile.

Example categories may include:

- General Throughput
- Scientific / Simulation
- Memory / Data Movement
- Encryption / Secure Data
- Visual / Creator Math

This helps users understand not just how fast the CPU is overall, but what kinds of workloads it appears best suited for.

### Output files

Depending on run options and version features, benchmark output may include:

- CSV benchmark result exports
- run log files
- system capability reports
- overall score summary files

These outputs make it easier to compare runs across different systems, settings, and future revisions.

### Notes for contributors and builders

- Version in this archive: **24.0.0**
- About dialog should match the application version
- Some benchmarks use hardware intrinsics, so older compiler/runtime combinations may behave differently
- If your system does not support a feature, that benchmark may not appear
- Intrinsics-heavy paths may behave differently across processors, BIOS settings, Windows scheduling behavior, and runtime versions
- NUMA-aware behavior may significantly affect scaling on multi-socket or multi-node systems

---

## v26 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v26.zip`  
**Program version:** `26.0.0`

### What changed in v26

Version **26.0.0** keeps the same overall benchmark project direction while adding a graph-focused usability improvement.

Added in v26:

- Per-series **show / hide buttons** for the fullscreen graph
- Quick **Show All** control
- Quick **Hide All** control
- Live graph redraw when visibility changes
- Better fullscreen graph interaction when many benchmark lines are present

In practical use, this means you can temporarily remove individual benchmark lines from the fullscreen chart so the graph is easier to read and compare.

This update is primarily a **graph usability update** and does not represent a major change to the benchmark engine itself.

### Build and usage note for v26

Build requirements remain the same as the v24 package unless the project files themselves specify otherwise in the archive.

### Notes for contributors and builders

- Version in this archive: **26.0.0**
- About dialog should match the application version
- v26 is mainly a fullscreen graph update
- The main new user-facing change is the ability to show or hide individual graph series quickly

---

## v27 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v27.zip`  
**Program version:** `27.0.0`

### What changed in v27

Version **27.0.0** keeps the earlier benchmark, scoring, and graphing direction while adding a more focused single-series graph explanation experience.

Added or improved in v27:

- The fullscreen graph keeps the **per-benchmark show / hide buttons** from v26
- When only **one benchmark line** is visible, the **right-side panel** now shows a focused explanation for that selected test
- The panel explains:
  - what the selected benchmark measures
  - what a healthy or expected scaling curve usually looks like
  - what the current run appears to be suggesting
- The focused text is meant to help the user understand whether the result looks more like:
  - good scaling
  - bandwidth or saturation behavior
  - partial scaling
  - something worth a closer look
- The graph view was updated so the fullscreen graph is not only interactive, but also more informative when isolating a single benchmark

In practical use, this means the fullscreen graph can now act more like a quick on-screen interpretation tool instead of only a raw line chart.

This update is mainly a **single-selected-benchmark graph analysis and explanation improvement** layered on top of the earlier fullscreen graph controls.

### Build and usage note for v27

Build requirements remain the same as the earlier packages unless the project files themselves specify otherwise in the archive.

### Notes for contributors and builders

- Version in this archive: **27.0.0**
- About dialog should match the application version
- v27 keeps the fullscreen graph controls from v26
- The main new user-facing change is the focused right-side analysis text when only one benchmark line is visible
- This makes it easier to understand the currently isolated benchmark without having to manually interpret the graph alone

---

## License

This project is released under the **MIT License** unless otherwise noted in the repository.

## Main repository

For the full project, documentation, and updates, see the main repository root.

