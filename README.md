# OpenPowertrain

**An open source ecosystem for powertrain development, simulation, validation and control.**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status: Experimental](https://img.shields.io/badge/status-experimental-red.svg)](#project-status)
[![Go Version](https://img.shields.io/badge/go-1.26%2B-00ADD8.svg)](https://go.dev)

---

## Project status

OpenPowertrain is still fully experimental and pre-alpha. There's no stable API yet, no versioned release, and the
architecture can still change a lot as the core simulation model gets validated. Right now this repo exists to build and
document one narrow proof of concept. Check [`ROADMAP.md`](./ROADMAP.md) to see exactly what that is.

## Mission

OpenPowertrain wants to become an open, extensible platform for powertrain engineering, covering everything from
thermodynamic and vehicle dynamics simulation to hardware in the loop testing, custom ECU development and hybrid
powertrain modeling. The core stays in Go. Specialized engineering tools like FreeCAD, OpenFOAM, CalculiX and
OpenModelica might get integrated later, once the core is mature enough to justify it.

## Why this project exists

Most powertrain simulation and calibration tools in the automotive industry are proprietary and closed. OpenPowertrain
is an attempt to build a technically rigorous and fully open alternative, grounded in established engineering references
like Heywood, Brunetti and the Bosch Automotive Handbook instead of reverse engineered guesswork.

## What's being built right now

The current focus is reproducing, in Go, the fundamental thermodynamics of the spark ignition (Otto) cycle: thermal
efficiency, P-V and P-α diagrams, torque, power and BSFC curves, all validated against classic references. There's also
a plan for a minimal Fyne desktop viewer to browse results locally without leaving the Go toolchain. Details live in [
`ROADMAP.md`](./ROADMAP.md).

## Getting started

Pre-alpha, so there's no stable build yet. This section gets filled in as the first deliverables land.

```bash
git clone https://github.com/augustoasilva/openpowertrain
cd openpowertrain
go build ./...
```

## Architecture

The core is organized as independent Go packages (`engine/`, `physics/`, `simulation/`, and so on), built so they can be
consumed by multiple front ends (CLI, HTTP API and eventually a Fyne desktop viewer) without duplicating logic. Full
design notes will live in [`docs/architecture.md`](./docs/architecture.md) as project progresses.

## Contributing

Check [`CONTRIBUTING.md`](./CONTRIBUTING.md) for how to propose changes, the commit sign-off requirement (DCO) and the
branching model.

## Governance

Right now OpenPowertrain is maintained by a single founder while the core gets validated. There's no formal governance
structure yet. If the project ever moves past the experimental phase, governance will probably evolve, possibly
including joining an existing open source foundation with neutral governance. This section gets updated if and when that
happens.

## License

OpenPowertrain is licensed under the [Apache License 2.0](./LICENSE). Hardware designs, once they exist, will be
licensed under [CERN-OHL-P](https://ohwr.org/cern_ohl_p_v2.txt). Documentation is licensed
under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
