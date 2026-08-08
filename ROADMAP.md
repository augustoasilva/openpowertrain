# OpenPowertrain — Roadmap

**Status: experimental.** This is deliberately narrow. It documents only the concrete, near-term deliverables being
built right now, not a long-term multi-phase plan. It'll get rewritten and expanded once this scope is validated.

## Current focus: Otto cycle thermodynamic simulation

The goal is to reproduce, in Go, the fundamental thermodynamic relationships of the spark-ignition (Otto) engine covered
in the introductory chapters of Brunetti (Vol. 1 and 2), cross-checked against Heywood. This is the foundation
everything else builds on.

### Planned outputs

- [ ] Ideal Otto cycle thermal efficiency as a function of compression ratio (η = 1 − 1/r^ (γ−1))
- [ ] P–V diagram (pressure by volume) for the ideal Otto cycle
- [ ] P–α diagram (pressure by crank angle), the indicated cycle
- [ ] Torque and power curves as a function of engine speed (RPM)
- [ ] Brake specific fuel consumption (BSFC) curve
- [ ] A comparison plot putting the model next to Brunetti's reference values and Heywood's reference values

### Approach

Core calculations live in Go (`engine/`, `physics/`) with no external dependencies for the math itself. Charts get
generated through `gonum/plot` and exported as PNG or SVG. There's also a plan for a minimal Fyne desktop viewer to
browse the generated charts locally, nothing close to a dashboard, just enough to see results without leaving the Go
toolchain.

### Reference literature

Brunetti, Franco — *Motores de Combustão Interna*, Vol. 1 and 2 (introductory chapters on thermodynamic cycles and
engine performance parameters)

Heywood, John B. — *Internal Combustion Engine Fundamentals*

## What comes after

Once this gets validated end to end (calculation, chart, comparison against reference data), the next milestone will be
scoped and documented here. No commitments beyond that yet.
